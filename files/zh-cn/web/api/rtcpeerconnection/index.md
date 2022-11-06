---
title: RTCPeerConnection
slug: Web/API/RTCPeerConnection
---

{{APIRef}}{{SeeCompatTable}}

**`RTCPeerConnection`** 接口代表一个由本地计算机到远端的 WebRTC 连接。该接口提供了创建，保持，监控，关闭连接的方法的实现。

> **备注：** `RTCPeerConnection` 和[`RTCSessionDescription`](/zh-CN/docs/Web/API/RTCSessionDescription) 是很多浏览器中使用的名称。强烈建议使用补充库，例如强大并且被广泛支持的[Adapter.js](https://github.com/webrtcHacks/adapter)，以确保您网站或 Web 应用程序的兼容性。值得注意的是[Adapter.js](https://github.com/webrtcHacks/adapter)不仅仅提供这些，它还做了一些其他补充以增强 WebRTC 在浏览器中的兼容性。参考：
>
> ```
> var PeerConnection = window.RTCPeerConnection || window.mozRTCPeerConnection || window.webkitRTCPeerConnection;
> var SessionDescription = window.RTCSessionDescription || window.mozRTCSessionDescription || window.webkitRTCSessionDescription;
> var GET_USER_MEDIA = navigator.getUserMedia ? "getUserMedia" :
>                      navigator.mozGetUserMedia ? "mozGetUserMedia" :
>                      navigator.webkitGetUserMedia ? "webkitGetUserMedia" : "getUserMedia";
> var v = document.createElement("video");
> var SRC_OBJECT = 'srcObject' in v ? "srcObject" :
>                  'mozSrcObject' in v ? "mozSrcObject" :
>                  'webkitSrcObject' in v ? "webkitSrcObject" : "srcObject";
> ```

由于 RTCPeerConnection 实现了 {{domxref("EventTarget")}} 接口，故其可以接收处理事件。

### 构造函数

- {{domxref("RTCPeerConnection.RTCPeerConnection()")}}
  - : 构造函数;创建一个新的 RTCPeerConnection 对象。

### 属性

_该接口的属性继承了其父接口，{{domxref("EventTarget")}}._

- {{domxref("RTCPeerConnection.canTrickleIceCandidates")}} {{ReadOnlyInline}}
  - : `如果远端支持 UDP 打洞或支持通过中继服务器连接，则该属性值为 true。否则，为 false。该属性的值依赖于远端设置且仅在本地的` {{domxref("RTCPeerConnection.setRemoteDescription()")}}方法被调用时有效，如果该方法没被调用，则其值为 null.
- {{domxref("RTCPeerConnection.connectionState")}} {{ReadOnlyInline}}
  - : 只读 connectionState 属性通过返回由枚举 RTCPeerConnectionState 指定的字符串值之一来指示对等连接的当前状态。
- {{domxref("RTCPeerConnection.currentLocalDescription")}} {{ReadOnlyInline}}
  - : 只读属性 RTCPeerConnection.currentLocalDescription 返回一个描述连接本地端的 RTCSessionDescription 对象，因为自上次 RTCPeerConnection 完成协商并连接到远程对等体之后，它最近成功协商。还包括可能已经由 ICE 代理生成的任何 ICE 候选者的列表，因为首先被描述的描述所表示的要约或答案。
- {{domxref("RTCPeerConnection.currentRemoteDescription")}} {{ReadOnlyInline}}
  - : 只读属性 RTCPeerConnection.currentRemoteDescription 返回一个 RTCSessionDescription 对象，描述连接的远程端，因为最近一次 RTCPeerConnection 完成协商并连接到远程对等体后最近成功协商。还包括可能已经由 ICE 代理生成的任何 ICE 候选者的列表，因为首先被描述的描述所表示的要约或答案。
- {{domxref("RTCPeerConnection.defaultIceServers")}} {{ReadOnlyInline}}
  - : 只读属性 RTCPeerConnection.defaultIceServers 根据 RTCIceServer 字典返回一个对象数组，该字典指示如果在 RTCConfiguration 中没有提供给 RTCPeerConnection 的默认情况下，浏览器将使用 ICE 服务器。然而，浏览器根本不需要提供任何默认的 ICE 服务器。
- {{domxref("RTCPeerConnection.iceConnectionState")}} {{ReadOnlyInline}}
  - : 只读属性 RTCPeerConnection.iceConnectionState 返回与 RTCPeerConnection 关联的 ICE 代理的状态类型为 RTCIceConnectionState 的枚举。
- {{domxref("RTCPeerConnection.iceGatheringState")}} {{ReadOnlyInline}}
  - : 只读属性，返回一个 RTCIceGatheringState 类型的结构体，它描述了连接的 ICE 收集状态
- {{domxref("RTCPeerConnection.localDescription")}} {{ReadOnlyInline}}
  - : 只读属性，返回一个 {{domxref("RTCSessionDescription")}} ，它描述了这条连接的本地端的会话控制（用户会话所需的属性以及配置信息）。如果本地的会话控制还没有被设置，它的值就会是 null。
- {{domxref("RTCPeerConnection.peerIdentity")}} {{ReadOnlyInline}}
  - : 只读属性，返回一个 `RTCIdentityAssertion`，它由一组信息构成，包括一个域名（idp）以及一个名称（name），它们代表了这条连接的远端机器的身份识别信息。如果远端机器还没有被设置以及校验，这个属性会返回一个 `null` 值。一旦被设置，它不能被一般方法改变。
- {{domxref("RTCPeerConnection.pendingLocalDescription")}} {{ReadOnlyInline}}
  - : 返回 {{DOMxRef("RTCSessionDescription")}} 对象，该对象展示连接本地端的待处理配置更改的信息。此函数并不是返回当前，而是在短期内可能存在的连接的信息。
- {{domxref("RTCPeerConnection.pendingRemoteDescription")}} {{ReadOnlyInline}}
  - : 返回 {{DOMxRef("RTCSessionDescription")}} 对象，该对象展示连接远程端的待处理配置更改的信息。此函数并不是返回当前，而是在短期内可能存在的连接的信息。
- {{domxref("RTCPeerConnection.remoteDescription")}} {{ReadOnlyInline}}
  - : 返回 {{DOMxRef("RTCSessionDescription")}} 对象，该对象展示连接远程端的，包括配置和媒体信息在内的会话的信息。如果尚未设置，则返回`null`。
- {{domxref("RTCPeerConnection.sctp")}} {{ReadOnlyInline}}
  - : 返回 {{DOMxRef("RTCSctpTransport")}} 对象，该对象展示发送和接收 {{Glossary("SCTP")}} 数据的 SCTP 传输层的信息。 如果尚未协商 SCTP，则此值为`null`。
- {{domxref("RTCPeerConnection.signalingState")}} {{ReadOnlyInline}}
  - : 返回一个 RTC 通信状态的结构体，这个结构体描述了本地连接的通信状态。这个 状态描述了一个定义连接配置的 SDP offer。它包含了下列信息，与{{domxref("MediaStream")}} 类型本地相关的对象的描述，媒体流编码方式或 RTP 和 RTCP 协议的选项，以及被 ICE 服务器收集到的 candidates(连接候选者)。当{{domxref("RTCPeerConnection.signalingState")}}的值改变时，对象上的{{event("signalingstatechange")}}事件会被触发。

### 基本用法

一个基本的 RTCPeerConnection 使用需要协调本地机器以及远端机器的连接，它可以通过在两台机器间生成 Session Description 的数据交换协议来实现。呼叫方发送一个 offer(请求)，被呼叫方发出一个 answer（应答）来回答请求。双方 - 呼叫方以及被呼叫方，最开始的时候都要建立他们各自的 RTCPeerConnection 对象。

```
var pc = new RTCPeerConnection();
pc.onaddstream = function(obj) {
  var vid = document.createElement("video");
  document.appendChild(vid);
  vid.srcObject = obj.stream;
}

// Helper functions
function endCall() {
  var videos = document.getElementsByTagName("video");
  for (var i = 0; i < videos.length; i++) {
    videos[i].pause();
  }

  pc.close();
}

function error(err) { endCall(); }
```

呼叫初始化

如果你是呼叫方，你需要初始化一个连接

```
// Get a list of friends from a server
// User selects a friend to start a peer connection with
navigator.getUserMedia({video: true}, function(stream) {
  pc.onaddstream({stream: stream});
  // Adding a local stream won't trigger the onaddstream callback
  pc.addStream(stream);

  pc.createOffer(function(offer) {
    pc.setLocalDescription(new RTCSessionDescription(offer), function() {
      // send the offer to a server to be forwarded to the friend you're calling.
    }, error);
  }, error);
})
```

呼叫回答

在另一端，你的朋友会从服务器收到 offer 信息。

```
var offer = getOfferFromFriend();
navigator.getUserMedia({video: true}, function(stream) {
  pc.onaddstream({stream: stream});
  pc.addStream(stream);

  pc.setRemoteDescription(new RTCSessionDescription(offer), function() {
    pc.createAnswer(function(answer) {
      pc.setLocalDescription(new RTCSessionDescription(answer), function() {
        // send the answer to a server to be forwarded back to the caller (you)
      }, error);
    }, error);
  }, error);
})
```

处理应答

同时在呼叫发起方，你会收到这个应答（前面被呼叫方发出的 answer），你需要将它设置为你的远端连接。

```
// pc was set up earlier when we made the original offer
var offer = getResponseFromFriend();
pc.setRemoteDescription(new RTCSessionDescription(offer), function() { }, error);
```

## 属性

_这个接口从它的父元素中继承属性，{{domxref("EventTarget")}}._

- {{domxref("RTCPeerConnection.iceConnectionState")}} {{ReadOnlyInline}}

  - : 返回一个 RTCIceConnectionState 类型的结构体，这个结构体描述了连接的 ICE 连接状态。当这个状态的值改变时，这个对象会触发一个{{event("iceconnectionstatechange")}} 事件。状态可能存在的值如下：

    - "new": ICE 服务器正在收集地址或正在等待远端的 candidates(这两种情况可能同时存在)。
    - `"checking"`: ICE 服务器找到了远端的 candidates（连接候选者）,这些 candidates 至少有一个，同时 ICE 服务器在检测这些 candidates，尽管它可能还没有找到连接。此刻，ICE 服务器可能仍在收集 candidates（连接候选者）。
    - `"connected"`: ICE 服务器已经找到了一条可用的适合所有组件的连接，但它仍然在测试更多的远端 candidate 以提供更好的连接。同时，ICE 服务器可能仍在收集 candidates。
    - `"completed"`: ICE 服务器已经找到了一条可用的连接，并不再测试远端 candidates。
    - `"failed"`: ICE 服务器已经检测了所有的远端 candidates，但并没有找到可用的。对一些组件适用的连接可能已经被找到。
    - `"disconnected"`: 至少一个组件的活跃度检查失败了，这可能是由糟糕的网络环境造成的一个短期状态，它可以被它自身所修复。
    - `"closed"`: ICE 服务器已经关闭，并不再响应请求。

- {{domxref("RTCPeerConnection.iceGatheringState")}} {{ReadOnlyInline}}

  - : 返回一个 iceGatheringState 类型的结构体，它描述了这条连接的 ICE 收集状态。该状态可能取以下的值：

    - `"new"`: 对象刚刚被创建，还没有网络化。
    - `"gathering"`: ICE 引擎正在为连接收集 candidates(连接候选者)。
    - `"complete"`: 引擎已经完成了 candidates 收集。但像添加一个新的接口或者一个新的 turn 服务器这些事件会导致状态回到"gathering"。

- {{domxref("RTCPeerConnection.localDescription")}} {{ReadOnlyInline}}
  - : 返回一个 {{domxref("RTCSessionDescription")}} ，它描述了这条连接的本地端的会话控制（用户会话所需的属性以及配置信息）。如果本地的会话控制还没有被设置，它的值就会是 null。
- {{domxref("RTCPeerConnection.peerIdentity")}} {{ReadOnlyInline}}
  - : 返回一个`RTCIdentityAssertion，它由一组信息构成，包括一个域名（idp）以及一个名称（name），它们代表了这条连接的远端机器的身份识别信息。如果远端机器还没有被设置以及校验，这个属性会返回一个 null 值。一旦被设置，它不能被一般方法改变`。
- {{domxref("RTCPeerConnection.remoteDescription")}} {{ReadOnlyInline}}
  - : 返回一个 {{domxref("RTCSessionDescription")}} 它描述了这条连接的远端机器的会话控制，如果远端机器还未被设置，它的值会是 null。
- {{domxref("RTCPeerConnection.signalingState")}} {{ReadOnlyInline}}

  - : 返回一个 RTC 通信状态的结构体，这个结构体描述了本地连接的通信状态。这个 状态描述了一个定义连接配置的 SDP offer。它包含了下列信息，与{{domxref("MediaStream")}} 类型本地相关的对象的描述，媒体流编码方式或 RTP 和 RTCP 协议的选项，以及被 ICE 服务器收集到的 candidates(连接候选者)。当{{domxref("RTCPeerConnection.signalingState")}}的值改变时，对象上的{{event("signalingstatechange")}}事件会被触发。它可能取下列的值：

    - `"stable"`: 没有 SDP offer/answer 正在被交换，连接仍然处于初始化状态。
    - `"have-local-offer"`: 这条连接的本地端机器已经本地应用了一个 SDP offer。
    - `"have-remote-offer"`: 这条连接的远端机器已经本地应用了一个 SDP offer。
    - `"have-local-pranswer"`: 一个来自远端的 SDP offer 已经被应用，同时一个 SDP pranswer 在本地被应用。
    - `"have-remote-pranswer"`：一个本地的 SDP offer 被应用，同时一个 SDP pranswer 在远端被应用。
    - `"closed"`: 连接被关闭。

### 事件处理器

- {{domxref("RTCPeerConnection.onaddstream")}}
  - : 是收到{{event("addstream")}} 事件时调用的事件处理器。Such an event is 当{{domxref("MediaStream")}} 被远端机器添加到这条连接时，该事件会被触发。当调用{{domxref("RTCPeerConnection.setRemoteDescription()")}}方法时，这个事件就会被立即触发，它不会等待 SDP 协商的结果。
- {{domxref("RTCPeerConnection.ondatachannel")}}
  - : 是收到{{event("datachannel")}} 事件时调用的事件处理器。当一个 {{domxref("RTCDataChannel")}} 被添加到连接时，这个事件被触发。
- {{domxref("RTCPeerConnection.onicecandidate")}}
  - : 是收到 {{event("icecandidate")}} 事件时调用的事件处理器.。当一个 {{domxref("RTCICECandidate")}} 对象被添加时，这个事件被触发。
- {{domxref("RTCPeerConnection.oniceconnectionstatechange")}}
  - : 是收到{{event("iceconnectionstatechange")}}事件时调用的事件处理器。当{{domxref("RTCPeerConnection.iceConnectionState", "iceConnectionState")}} 改变时，这个事件被触发。
- {{domxref("RTCPeerConnection.onidentityresult")}}
  - : 是收到 {{event("identityresult")}}事件时调用的事件处理器。当通过{{domxref("RTCPeerConnection.getIdentityAssertion()", "getIdentityAssertion()")}}生成身份断言，或在生成一个 answer 或一个 offer 的过程中，这个事件被触发。
- {{domxref("RTCPeerConnection.onidpassertionerror")}}
  - : 是收到 {{event("idpassertionerror")}} 事件时调用的事件处理器。当生成一个身份断言时，如果关联的身份提供者（idP）遇到一个错误，这个事件就会被触发。
- {{domxref("RTCPeerConnection.onidpvalidationerror")}}
  - : 是收到 {{event("idpvalidationerror")}} 事件时调用的事件处理器。当检查 一个身份断言时，如果关联的身份提供者（idP）遇到一个错误，这个事件就会被触发。
- {{domxref("RTCPeerConnection.onnegotiationneeded")}}
  - : 是收到{{event("negotiationneeded")}} 事件时调用的事件处理器，浏览器发送该事件以告知在将来某一时刻需要协商。
- {{domxref("RTCPeerConnection.onpeeridentity")}}
  - : 是收到{{event("peeridentity")}} 事件时调用的事件处理器，当一条连接的 peer identify 被设置以及校验后，该事件被触发
- {{domxref("RTCPeerConnection.onremovestream")}}
  - : 是收到{{event("removestream")}} 事件时调用的事件处理器，当一条{{domxref("MediaStream")}} 从连接上移除时，该事件被触发。
- {{domxref("RTCPeerConnection.onsignalingstatechange")}}
  - : 是收到{{event("signalingstatechange")}} 事件时调用的事件处理器，当{{domxref("RTCPeerConnection.signalingState", "signalingState")}}的值发生改变时，该事件被触发。

## 方法

- {{domxref("RTCPeerConnection.RTCPeerConnection", "RTCPeerConnection()")}}
  - : RTCPeerConnection 的初始化函数，通过 new RTCPeerConnection() 初始化一个 RTCPeerConnection 实例。
- {{domxref("RTCPeerConnection.createOffer()")}}
  - : 生成一个 offer，它是一个带有特定的配置信息寻找远端匹配机器（peer）的请求。这个方法的前两个参数分别是方法调用成功以及失败的回调函数，可选的第三个参数是用户对视频流以及音频流的定制选项（一个对象）。
- {{domxref("RTCPeerConnection.createAnswer()")}}
  - : 在协调一条连接中的两端 offer/answers 时，根据从远端发来的 offer 生成一个 answer。这个方法的前两个参数分别是方法调用成功以及失败时的回调函数，可选的第三个参数是生成的 answer 的可供选项。
- {{domxref("RTCPeerConnection.setLocalDescription()")}}
  - : 改变与连接相关的本地描述。这个描述定义了连接的属性，例如：连接的编码方式。连接会受到它的改变的影响，而且连接必须能同时支持新的以及旧的描述。这个方法可以接收三个参数，一个{{domxref("RTCSessionDescription")}} 对象包含设置信息，还有两个回调函数，它们分别是方法调用成功以及失败的回调函数。
- {{domxref("RTCPeerConnection.setRemoteDescription()")}}
  - : 改变与连接相关的远端描述。这个描述定义了连接的属性，例如：连接的编码方式。连接会受到它的改变的影响，而且连接必须能同时支持新的以及旧的描述。这个方法可以接收三个参数，一个{{domxref("RTCSessionDescription")}} 对象包含设置信息，还有两个回调函数，它们分别是方法调用成功以及失败的回调函数。
- {{domxref("RTCPeerConnection.updateIce()")}}
  - : 更新 ICE 服务器时调用的方法。
- {{domxref("RTCPeerConnection.addIceCandidate()")}}
  - : 添加 iceCandidate 时调用的方法。
- {{domxref("RTCPeerConnection.getConfiguration()")}}
  - : 获取配置信息时调用的方法。
- {{domxref("RTCPeerConnection.getLocalStreams()")}}
  - : 返回连接的本地媒体流数组。这个数组可能是空数组。
- {{domxref("RTCPeerConnection.getRemoteStreams()")}}
  - : 返回连接的远端媒体流数组。这个数组可能是空数组。
- {{domxref("RTCPeerConnection.getStreamById()")}}
  - : 返回连接中与所给 id 匹配的媒体流 {{domxref("MediaStream")}}，如果没有匹配项，返回 null。
- {{domxref("RTCPeerConnection.addStream()")}}
  - : 添加一个媒体流 {{domxref("MediaStream")}}作为本地音频或视频源。如果本地端与远端协调已经发生了，那么需要一个新的媒体流，这样远端才可以使用它。
- {{domxref("RTCPeerConnection.removeStream()")}}
  - : 将一个作为本地音频或视频源的媒体流 {{domxref("MediaStream")}}移除。如果本地端与远端协调已经发生了，那么需要一个新的媒体流，这样远端才可以停止使用它。
- {{domxref("RTCPeerConnection.close()")}}
  - : 关闭一个 RTCPeerConnection 实例所调用的方法。
- {{domxref("RTCPeerConnection.createDataChannel()")}}
  - : 在一条连接上建立一个新的{{domxref("RTCDataChannel")}}（用于数据发送）。这个方法把一个数据对象作为参数，数据对象中包含必要的配置信息。
- {{domxref("RTCPeerConnection.createDTMFSender()")}}
  - : 创建一个新的与特殊的{{domxref("MediaStreamTrack")}}相关的{{domxref("RTCDTMFSender")}}，可以在连接上发送{{Glossary("DTMF")}}手机信号。
- {{domxref("RTCPeerConnection.getStats()")}}
  - : 生成一个新的{{domxref("RTCStatsReport")}}，它包含连接相关的统计信息。
- {{domxref("RTCPeerConnection.setIdentityProvider()")}}
  - : 根据所给的三个参数设置身份提供者（IdP)，这三个参数是它的名称，通信所使用的协议（可选），以及一个可选的用户名。只有当一个断言被需要时，这个 IdP 才会被使用。
- {{domxref("RTCPeerConnection.getIdentityAssertion()")}}
  - : 初始化身份断言的收集，只有当{{domxref("RTCPeerConnection.signalingState", "signalingState")}}的值不为"closed"时，它才有效。它自动完成，在需求发生前调用它是最好的选择。

### 构造函数

```
new RTCPeerConnection({{domxref("RTCConfiguration")}} configuration, optional {{domxref("MediaConstraints")}} constraints);
```

> **备注：** PeerConnection 需要传递一个 RTCConfiguration 对象作为参数，如果你没有传递参数的话，火狐浏览器会自动提供一个参数。

## 方法

### createOffer

`void createOffer({{domxref("RTCSessionDescriptionCallback")}} successCallback, {{domxref("RTCPeerConnectionErrorCallback")}} failureCallback, optional {{domxref("MediaConstraints")}} constraints);`

createOffer 方法会生成描述信息的一个 blob 对象，它会帮助连接到本地机器。当你已经找到一个远端的 PeerConnection 并且打算设置建立本地的 PeerConnection 时，你可以使用该方法。

#### 举例

```
var pc = new PeerConnection();
pc.addStream(video);
pc.createOffer(function(desc){
  pc.setLocalDescription(desc, function() {
    // send the offer to a server that can negotiate with a remote client
  });
}
```

#### 参数

- successCallback（方法调用成功时的回调函数）
  - : 一个 {{domxref("RTCSessionDescriptionCallback")}} 它会收到一个 {{domxref("RTCSessionDescription")}} 对象作为参数。
- errorCallback（方法调用失败时的回调函数）
  - : 一个 {{domxref("RTCPeerConnectionErrorCallback")}} 它会收到一个 {{domxref("DOMError")}} 对象作为参数。
- \[optional] constraints(可选的约束条件)
  - : 一个可选的{{domxref("MediaConstraints")}} 对象。

### createAnswer

`void createAnswer({{domxref("RTCSessionDescriptionCallback")}} successCallback, {{domxref("RTCPeerConnectionErrorCallback")}} failureCallback, optional {{domxref("MediaConstraints")}} constraints)")`

对从远方收到的 offer 进行回答。

#### 举例

```
var pc = new PeerConnection();
pc.setRemoteDescription(new RTCSessionDescription(offer), function() {
  pc.createAnswer(function(answer) {
    pc.setLocalDescription(answer, function() {
      // send the answer to the remote connection
    })
  })
});
```

#### 参数

- successCallback（方法调用成功时的回调函数）
  - : 一个 {{domxref("RTCSessionDescriptionCallback")}} 它会收到一个 {{domxref("RTCSessionDescription")}} 对象作为参数。
- errorCallback（方法调用失败时的回调函数）
  - : 一个 {{domxref("RTCPeerConnectionErrorCallback")}} 它会收到一个{{domxref("DOMError")}} 对象作为参数。
- \[optional] constraints（可选的约束条件）
  - : 一个可选的{{domxref("MediaConstraints")}} 对象。

### updateIce()

updateIce(optional {{domxref("RTCConfiguration")}} configuration, optional {{domxref("MediaConstraints")}} constraints)

该方法会更新 ICE 代理收集本地 candidates 以及连接云端 candidates 的进程。如果强制约束条件"IceTransports"存在，那么它会控制 ICE 代理的工作方式。它可以用于限制接听者对 TURN candidates 的使用，这样可以避免在请求被应答前泄露位置信息。如果这个方法影响了已经建立的连接，那么它可能导致 ICE 代理状态的改变以及媒体状态的改变。

#### 举例

### addIceCandidate()

addIceCandidate ({{domxref("RTCIceCandidate")}} candidate, {{domxref("Function")}} successCallback, {{domxref("RTCPeerConnectionErrorCallback")}} failureCallback);

除了被添加到远端描述之外，只要约束条件"IceTransports" 没有被设置为 null，连接检测结果会被发送给新的 candidates。如果这个方法影响了已经建立的连接，那么它可能导致 ICE 代理状态的改变以及媒体状态的改变。

#### 举例

```js
pc.addIceCandidate(new RTCIceCandidate(candidate));
```

### createDataChannel

`{{domxref("RTCDataChannel")}} createDataChannel ({{domxref("DOMString")}} label, optional {{domxref("RTCDataChannelInit")}} dataChannelDict);`

通过 peerconnection 建立一条数据信道，用于发送非视频音频信息。

#### 例子

```
var pc = new PeerConnection();
var channel = pc.createDataChannel("Mydata");
channel.onopen = function(event) {
  channel.send('sending a message');
}
channel.onmessage = function(event) { console.log(event.data); }
```

## 引申阅读

- <https://github.com/jesup/nightly-gupshup/blob/master/static/js/chat.js>
- <http://www.html5rocks.com/en/tutorials/webrtc/basics/#toc-simple>
- <http://dev.w3.org/2011/webrtc/editor/webrtc.html>
