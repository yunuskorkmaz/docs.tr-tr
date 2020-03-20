---
title: Ek sınıf kitaplıkları ve API'ler
ms.date: 11/19/2019
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
ms.topic: conceptual
ms.openlocfilehash: abf7fd20988ebaaaf1a40ccc168c636fd0dacc1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155914"
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="d74f8-102">Ek sınıf kitaplıkları ve API'ler</span><span class="sxs-lookup"><span data-stu-id="d74f8-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="d74f8-103">.NET Framework sürekli gelişmektedir.</span><span class="sxs-lookup"><span data-stu-id="d74f8-103">The .NET Framework is constantly evolving.</span></span> <span data-ttu-id="d74f8-104">Platformlar arası geliştirmeyi geliştirmek ve yeni işlevleri erken tanıtmak için, yeni özellikler banttan (OOB) çıkar.</span><span class="sxs-lookup"><span data-stu-id="d74f8-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span></span> <span data-ttu-id="d74f8-105">Bu konu, dokümantasyon sağladığımız OOB projelerini listeler.</span><span class="sxs-lookup"><span data-stu-id="d74f8-105">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="d74f8-106">Ayrıca, bazı kitaplıklar .NET Framework'ün belirli platformlarını veya uygulamalarını hedef alır.</span><span class="sxs-lookup"><span data-stu-id="d74f8-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="d74f8-107">Örneğin, <xref:System.Text.CodePagesEncodingProvider> sınıf kod sayfası kodlamalarını .NET Framework kullanılarak geliştirilen UWP uygulamalarında kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="d74f8-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="d74f8-108">Bu konu, bu kitaplıkları da listeler.</span><span class="sxs-lookup"><span data-stu-id="d74f8-108">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="d74f8-109">OOB projeleri</span><span class="sxs-lookup"><span data-stu-id="d74f8-109">OOB projects</span></span>
  
| <span data-ttu-id="d74f8-110">Project</span><span class="sxs-lookup"><span data-stu-id="d74f8-110">Project</span></span> | <span data-ttu-id="d74f8-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d74f8-111">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="d74f8-112">İş parçacığı güvenli ve içeriğini asla değiştirmez garanti koleksiyonları sağlar.</span><span class="sxs-lookup"><span data-stu-id="d74f8-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="d74f8-113">Windows'un WinHTTP <xref:System.Net.Http.HttpClient> arabirimini temel alan bir ileti işleyicisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d74f8-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="d74f8-114">SIMD donanım tabanlı ivmeden yararlanabilecek vektör türlerinin kitaplıklarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d74f8-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>|
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="d74f8-115">TPL Dataflow Kitaplığı, eşzamanlılık özellikli uygulamaların sağlamlığını artırmaya yardımcı olmak için veri akışı bileşenleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d74f8-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="d74f8-116">Platforma özel kütüphaneler</span><span class="sxs-lookup"><span data-stu-id="d74f8-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="d74f8-117">Project</span><span class="sxs-lookup"><span data-stu-id="d74f8-117">Project</span></span> | <span data-ttu-id="d74f8-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d74f8-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="d74f8-119">Evrensel Windows <xref:System.Text.EncodingProvider> Platformu'nu hedefleyen uygulamalar için kod sayfası kodlamalarını kullanılabilir hale getirmek için sınıfı genişletir.</span><span class="sxs-lookup"><span data-stu-id="d74f8-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="d74f8-120">Özel API'ler</span><span class="sxs-lookup"><span data-stu-id="d74f8-120">Private APIs</span></span>  

<span data-ttu-id="d74f8-121">Bu API'ler ürün altyapısını destekler ve doğrudan kodunuzdakullanılmak üzere tasarlanmamıştır/desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d74f8-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
* [<span data-ttu-id="d74f8-122">Microsoft.SqlServer.Server.SmiOrderProperty.Item Özellik</span><span class="sxs-lookup"><span data-stu-id="d74f8-122">Microsoft.SqlServer.Server.SmiOrderProperty.Item Property</span></span>](microsoft.sqlserver.server.smiorderproperty.item.md)
* [<span data-ttu-id="d74f8-123">System.Exception.PrepForRemoting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d74f8-123">System.Exception.PrepForRemoting Method</span></span>](system.exception.prepforremoting.md)
* [<span data-ttu-id="d74f8-124">System.Data.SqlTypes.SqlChars.Stream Özelliği</span><span class="sxs-lookup"><span data-stu-id="d74f8-124">System.Data.SqlTypes.SqlChars.Stream Property</span></span>](system.data.sqltypes.sqlchars.stream.md)
* [<span data-ttu-id="d74f8-125">System.Data.SqlTypes.SqlStreamChars Constructor</span><span class="sxs-lookup"><span data-stu-id="d74f8-125">System.Data.SqlTypes.SqlStreamChars Constructor</span></span>](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [<span data-ttu-id="d74f8-126">System.Data.SqlTypes.SqlStreamChars.CanSeek Özelliği</span><span class="sxs-lookup"><span data-stu-id="d74f8-126">System.Data.SqlTypes.SqlStreamChars.CanSeek Property</span></span>](system.data.sqltypes.sqlstreamchars.canseek.md)
* [<span data-ttu-id="d74f8-127">System.Data.SqlTypes.SqlStreamChars.IsNull Özelliği</span><span class="sxs-lookup"><span data-stu-id="d74f8-127">System.Data.SqlTypes.SqlStreamChars.IsNull Property</span></span>](system.data.sqltypes.sqlstreamchars.isnull.md)
* [<span data-ttu-id="d74f8-128">System.Data.SqlTypes.SqlStreamChars.Length Özelliği</span><span class="sxs-lookup"><span data-stu-id="d74f8-128">System.Data.SqlTypes.SqlStreamChars.Length Property</span></span>](system.data.sqltypes.sqlstreamchars.length.md)
* [<span data-ttu-id="d74f8-129">System.Data.SqlTypes.SqlStreamChars.Close Metodu</span><span class="sxs-lookup"><span data-stu-id="d74f8-129">System.Data.SqlTypes.SqlStreamChars.Close Method</span></span>](system.data.sqltypes.sqlstreamchars.close.md)
* [<span data-ttu-id="d74f8-130">System.Data.SqlTypes.SqlStreamChars.Dispose Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d74f8-130">System.Data.SqlTypes.SqlStreamChars.Dispose Method</span></span>](system.data.sqltypes.sqlstreamchars.dispose.md)
* [<span data-ttu-id="d74f8-131">System.Data.SqlTypes.SqlStreamChars.Flush Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d74f8-131">System.Data.SqlTypes.SqlStreamChars.Flush Method</span></span>](system.data.sqltypes.sqlstreamchars.flush.md)
* [<span data-ttu-id="d74f8-132">System.Data.SqlTypes.SqlStreamChars.Read Metodu</span><span class="sxs-lookup"><span data-stu-id="d74f8-132">System.Data.SqlTypes.SqlStreamChars.Read Method</span></span>](system.data.sqltypes.sqlstreamchars.read.md)
* [<span data-ttu-id="d74f8-133">System.Data.SqlTypes.SqlStreamChars.Seek Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d74f8-133">System.Data.SqlTypes.SqlStreamChars.Seek Method</span></span>](system.data.sqltypes.sqlstreamchars.seek.md)
* [<span data-ttu-id="d74f8-134">System.Data.SqlTypes.SqlStreamChars.SetLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d74f8-134">System.Data.SqlTypes.SqlStreamChars.SetLength Method</span></span>](system.data.sqltypes.sqlstreamchars.setlength.md)
* [<span data-ttu-id="d74f8-135">System.Data.SqlTypes.SqlStreamChars.Write Metodu</span><span class="sxs-lookup"><span data-stu-id="d74f8-135">System.Data.SqlTypes.SqlStreamChars.Write Method</span></span>](system.data.sqltypes.sqlstreamchars.write.md)
* [<span data-ttu-id="d74f8-136">System.io.MemoryStream.internalgetoriginandlength yöntemi</span><span class="sxs-lookup"><span data-stu-id="d74f8-136">System.IO.MemoryStream.InternalGetOriginAndLength Method</span></span>](system.io.memorystream.internalgetoriginandlength.md)
* [<span data-ttu-id="d74f8-137">System.Net.Connection Sınıfı</span><span class="sxs-lookup"><span data-stu-id="d74f8-137">System.Net.Connection Class</span></span>](connection.md)
* [<span data-ttu-id="d74f8-138">System.Net.Connection.m\_YazmaListesi Alanı</span><span class="sxs-lookup"><span data-stu-id="d74f8-138">System.Net.Connection.m\_WriteList Field</span></span>](m_writelist.md)
* [<span data-ttu-id="d74f8-139">System.Net.ConnectionGroup Sınıfı</span><span class="sxs-lookup"><span data-stu-id="d74f8-139">System.Net.ConnectionGroup Class</span></span>](connectiongroup.md)
* [<span data-ttu-id="d74f8-140">System.Net.ConnectionGroup.m\_ConnectionList Alanı</span><span class="sxs-lookup"><span data-stu-id="d74f8-140">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](m_connectionlist.md)
* [<span data-ttu-id="d74f8-141">System.Net.ConnectStream.Connection Özelliği</span><span class="sxs-lookup"><span data-stu-id="d74f8-141">System.Net.ConnectStream.Connection Property</span></span>](system.net.connectstream.connection.md)
* [<span data-ttu-id="d74f8-142">System.Net.CoreResponseData Sınıfı</span><span class="sxs-lookup"><span data-stu-id="d74f8-142">System.Net.CoreResponseData Class</span></span>](coreresponsedata.md)
* [<span data-ttu-id="d74f8-143">System.Net.CoreResponseData.m\_ResponseHeaders Alanı</span><span class="sxs-lookup"><span data-stu-id="d74f8-143">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](coreresponsedata_m_responseheaders.md)
* [<span data-ttu-id="d74f8-144">System.Net.CoreResponseData.m\_StatusCode Alanı</span><span class="sxs-lookup"><span data-stu-id="d74f8-144">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](coreresponsedata_m_statuscode.md)
* [<span data-ttu-id="d74f8-145">System.Net.httpWebRequest. \_AutoRedirects Alanı</span><span class="sxs-lookup"><span data-stu-id="d74f8-145">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](_autoredirects.md)
* [<span data-ttu-id="d74f8-146">System.Net.httpWebRequest. \_CoreResponse Alanı</span><span class="sxs-lookup"><span data-stu-id="d74f8-146">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](httpwebrequest__coreresponse.md)
* [<span data-ttu-id="d74f8-147">System.Net.httpWebRequest. \_httpResponse Alanı</span><span class="sxs-lookup"><span data-stu-id="d74f8-147">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](_httpresponse.md)
* [<span data-ttu-id="d74f8-148">System.Net.PooledStream.NetworkStream Özelliği</span><span class="sxs-lookup"><span data-stu-id="d74f8-148">System.Net.PooledStream.NetworkStream Property</span></span>](system.net.pooledstream.networkstream.md)
* [<span data-ttu-id="d74f8-149">System.Net.RtcState sınıfı</span><span class="sxs-lookup"><span data-stu-id="d74f8-149">System.Net.RtcState class</span></span>](system.net.rtcstate.md)
* [<span data-ttu-id="d74f8-150">System.Net.ServicePoint.m\_ConnectionGroupList Alanı</span><span class="sxs-lookup"><span data-stu-id="d74f8-150">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](m_connectiongrouplist.md)
* [<span data-ttu-id="d74f8-151">System.Net.ServicePointManager.s\_ServicePointTable Alanı</span><span class="sxs-lookup"><span data-stu-id="d74f8-151">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](s_servicepointtable.md)
* [<span data-ttu-id="d74f8-152">System.Net.TlsStream.m_Worker Alanı</span><span class="sxs-lookup"><span data-stu-id="d74f8-152">System.Net.TlsStream.m_Worker Field</span></span>](system.net.tlsstream.m_worker.md)
* [<span data-ttu-id="d74f8-153">System.Net.Security.SslState.SslProtocol Özelliği</span><span class="sxs-lookup"><span data-stu-id="d74f8-153">System.Net.Security.SslState.SslProtocol Property</span></span>](system.net.security.sslstate.sslprotocol.md)
* [<span data-ttu-id="d74f8-154">System.ServiceModel.Channels.Message.BodyToString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d74f8-154">System.ServiceModel.Channels.Message.BodyToString Method</span></span>](system.servicemodel.channels.message.bodytostring.md)
* [<span data-ttu-id="d74f8-155">System.ServiceModel.Channels.Message.WriteStartHeaders Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d74f8-155">System.ServiceModel.Channels.Message.WriteStartHeaders Method</span></span>](system.servicemodel.channels.message.writestartheaders.md)
* [<span data-ttu-id="d74f8-156">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Alan</span><span class="sxs-lookup"><span data-stu-id="d74f8-156">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [<span data-ttu-id="d74f8-157">System.Windows.Forms.Design.DataMemberFieldEditor Sınıfı</span><span class="sxs-lookup"><span data-stu-id="d74f8-157">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](datamemberfieldeditor-class.md)
* [<span data-ttu-id="d74f8-158">System.Windows.Forms.Design.DataMemberListEditor Sınıfı</span><span class="sxs-lookup"><span data-stu-id="d74f8-158">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](datamemberlisteditor-class.md)
* [<span data-ttu-id="d74f8-159">System.Xml.XmlReader.CreateSqlReader Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d74f8-159">System.Xml.XmlReader.CreateSqlReader Method</span></span>](system.xml.xmlreader.createsqlreader.md)
* [<span data-ttu-id="d74f8-160">Adodb. Bağlantı Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d74f8-160">adodb.Connection Interface</span></span>](adodb.connection.md)
* [<span data-ttu-id="d74f8-161">Adodb. OlayReason Enum</span><span class="sxs-lookup"><span data-stu-id="d74f8-161">adodb.EventReason Enum</span></span>](adodb.eventreasonenum.md)
* [<span data-ttu-id="d74f8-162">Adodb. OlayDurum Enum</span><span class="sxs-lookup"><span data-stu-id="d74f8-162">adodb.EventStatus Enum</span></span>](adodb.eventstatusenum.md)
* [<span data-ttu-id="d74f8-163">stdole. DISPPARAMS Yapısı</span><span class="sxs-lookup"><span data-stu-id="d74f8-163">stdole.DISPPARAMS Structure</span></span>](stdole.dispparams.md)
* [<span data-ttu-id="d74f8-164">stdole. EXCEPINFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="d74f8-164">stdole.EXCEPINFO Structure</span></span>](stdole.excepinfo.md)
* [<span data-ttu-id="d74f8-165">stdole. IFont.Name Özelliği</span><span class="sxs-lookup"><span data-stu-id="d74f8-165">stdole.IFont.Name Property</span></span>](stdole.ifont.name.md)
* [<span data-ttu-id="d74f8-166">stdole. IFontDisp Arayüzü</span><span class="sxs-lookup"><span data-stu-id="d74f8-166">stdole.IFontDisp Interface</span></span>](stdole.ifontdisp.md)
* [<span data-ttu-id="d74f8-167">stdole. IPicture.Handle Özelliği</span><span class="sxs-lookup"><span data-stu-id="d74f8-167">stdole.IPicture.Handle Property</span></span>](stdole.ipicture.handle.md)
* [<span data-ttu-id="d74f8-168">stdole. IPictureDisp.Handle Özelliği</span><span class="sxs-lookup"><span data-stu-id="d74f8-168">stdole.IPictureDisp.Handle Property</span></span>](stdole.ipicturedisp.handle.md)
* [<span data-ttu-id="d74f8-169">stdole. StdFont Arayüzü</span><span class="sxs-lookup"><span data-stu-id="d74f8-169">stdole.StdFont Interface</span></span>](stdole.stdfont.md)
* [<span data-ttu-id="d74f8-170">stdole. StdPicture Arayüzü</span><span class="sxs-lookup"><span data-stu-id="d74f8-170">stdole.StdPicture Interface</span></span>](stdole.stdpicture.md)
  
## <a name="see-also"></a><span data-ttu-id="d74f8-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d74f8-171">See also</span></span>

* [<span data-ttu-id="d74f8-172">.NET Framework ve Bant Dışı Yayınlar</span><span class="sxs-lookup"><span data-stu-id="d74f8-172">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
