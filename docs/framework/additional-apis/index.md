---
title: Ek sınıf kitaplıkları ve API'ler
ms.date: 11/19/2019
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: e1e2af584c73b1c0b2548cdd3fcbd8517dfa330d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429344"
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="d7c96-102">Ek sınıf kitaplıkları ve API'ler</span><span class="sxs-lookup"><span data-stu-id="d7c96-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="d7c96-103">.NET Framework sürekli olarak gelişiyor.</span><span class="sxs-lookup"><span data-stu-id="d7c96-103">The .NET Framework is constantly evolving.</span></span> <span data-ttu-id="d7c96-104">Platformlar arası geliştirmeyi artırmak ve yeni işlevselliği erken sunmak için yeni özellikler bant dışı (OOB) olarak serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="d7c96-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span></span> <span data-ttu-id="d7c96-105">Bu konu, için belge sağlamamız gereken OOB projelerini listeler.</span><span class="sxs-lookup"><span data-stu-id="d7c96-105">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="d7c96-106">Ayrıca, bazı kitaplıklar belirli platformları veya .NET Framework uygulamalarını hedeflemelidir.</span><span class="sxs-lookup"><span data-stu-id="d7c96-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="d7c96-107">Örneğin <xref:System.Text.CodePagesEncodingProvider> sınıfı, kod sayfası kodlamalarını .NET Framework kullanılarak geliştirilen UWP uygulamaları için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="d7c96-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="d7c96-108">Bu konu başlığı altında da bu kitaplıklar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="d7c96-108">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="d7c96-109">OOB projeleri</span><span class="sxs-lookup"><span data-stu-id="d7c96-109">OOB projects</span></span>
  
| <span data-ttu-id="d7c96-110">Proje</span><span class="sxs-lookup"><span data-stu-id="d7c96-110">Project</span></span> | <span data-ttu-id="d7c96-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7c96-111">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="d7c96-112">, İş parçacığı açısından güvenli olan ve içeriklerinin hiçbir şekilde değişmeme garantisi sağlayan koleksiyonlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7c96-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="d7c96-113">Windows 'un WinHTTP arabirimine göre <xref:System.Net.Http.HttpClient> için bir ileti işleyicisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7c96-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="d7c96-114">SıMD donanım tabanlı hızlandırmasının avantajlarından yararlanan bir vektör türleri kitaplığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7c96-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="d7c96-115">TPL veri akışı kitaplığı, eşzamanlılık özellikli uygulamaların sağlamlığını artırmaya yardımcı olmak için veri akışı bileşenleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d7c96-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="d7c96-116">Platforma özgü kitaplıklar</span><span class="sxs-lookup"><span data-stu-id="d7c96-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="d7c96-117">Proje</span><span class="sxs-lookup"><span data-stu-id="d7c96-117">Project</span></span> | <span data-ttu-id="d7c96-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7c96-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="d7c96-119">Kod sayfası kodlamalarını Evrensel Windows Platformu hedefleyen uygulamalar için kullanılabilir hale getirmek için <xref:System.Text.EncodingProvider> sınıfını genişletir.</span><span class="sxs-lookup"><span data-stu-id="d7c96-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="d7c96-120">Özel API 'Ler</span><span class="sxs-lookup"><span data-stu-id="d7c96-120">Private APIs</span></span>  

<span data-ttu-id="d7c96-121">Bu API 'Ler ürün altyapısını destekler ve doğrudan kodunuzdan kullanılmak üzere tasarlanmamıştır/desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d7c96-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
* [<span data-ttu-id="d7c96-122">Microsoft. SqlServer. Server. Smorderproperty. Item özelliği</span><span class="sxs-lookup"><span data-stu-id="d7c96-122">Microsoft.SqlServer.Server.SmiOrderProperty.Item Property</span></span>](microsoft.sqlserver.server.smiorderproperty.item.md)
* [<span data-ttu-id="d7c96-123">System. Exception. PrepForRemoting yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7c96-123">System.Exception.PrepForRemoting Method</span></span>](system.exception.prepforremoting.md)
* [<span data-ttu-id="d7c96-124">System. Data. SqlTypes. SqlChars. Stream özelliği</span><span class="sxs-lookup"><span data-stu-id="d7c96-124">System.Data.SqlTypes.SqlChars.Stream Property</span></span>](system.data.sqltypes.sqlchars.stream.md)
* [<span data-ttu-id="d7c96-125">System. Data. SqlTypes. SqlStreamChars Oluşturucusu</span><span class="sxs-lookup"><span data-stu-id="d7c96-125">System.Data.SqlTypes.SqlStreamChars Constructor</span></span>](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [<span data-ttu-id="d7c96-126">System. Data. SqlTypes. SqlStreamChars. CanSeek özelliği</span><span class="sxs-lookup"><span data-stu-id="d7c96-126">System.Data.SqlTypes.SqlStreamChars.CanSeek Property</span></span>](system.data.sqltypes.sqlstreamchars.canseek.md)
* [<span data-ttu-id="d7c96-127">System. Data. SqlTypes. SqlStreamChars. IsNull Özelliği</span><span class="sxs-lookup"><span data-stu-id="d7c96-127">System.Data.SqlTypes.SqlStreamChars.IsNull Property</span></span>](system.data.sqltypes.sqlstreamchars.isnull.md)
* [<span data-ttu-id="d7c96-128">System. Data. SqlTypes. SqlStreamChars. length özelliği</span><span class="sxs-lookup"><span data-stu-id="d7c96-128">System.Data.SqlTypes.SqlStreamChars.Length Property</span></span>](system.data.sqltypes.sqlstreamchars.length.md)
* [<span data-ttu-id="d7c96-129">System. Data. SqlTypes. SqlStreamChars. Close yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7c96-129">System.Data.SqlTypes.SqlStreamChars.Close Method</span></span>](system.data.sqltypes.sqlstreamchars.close.md)
* [<span data-ttu-id="d7c96-130">System. Data. SqlTypes. SqlStreamChars. Dispose yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7c96-130">System.Data.SqlTypes.SqlStreamChars.Dispose Method</span></span>](system.data.sqltypes.sqlstreamchars.dispose.md)
* [<span data-ttu-id="d7c96-131">System. Data. SqlTypes. SqlStreamChars. Flush yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7c96-131">System.Data.SqlTypes.SqlStreamChars.Flush Method</span></span>](system.data.sqltypes.sqlstreamchars.flush.md)
* [<span data-ttu-id="d7c96-132">System. Data. SqlTypes. SqlStreamChars. Read yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7c96-132">System.Data.SqlTypes.SqlStreamChars.Read Method</span></span>](system.data.sqltypes.sqlstreamchars.read.md)
* [<span data-ttu-id="d7c96-133">System. Data. SqlTypes. SqlStreamChars. Seek yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7c96-133">System.Data.SqlTypes.SqlStreamChars.Seek Method</span></span>](system.data.sqltypes.sqlstreamchars.seek.md)
* [<span data-ttu-id="d7c96-134">System. Data. SqlTypes. SqlStreamChars. SetLength yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7c96-134">System.Data.SqlTypes.SqlStreamChars.SetLength Method</span></span>](system.data.sqltypes.sqlstreamchars.setlength.md)
* [<span data-ttu-id="d7c96-135">System. Data. SqlTypes. SqlStreamChars. Write yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7c96-135">System.Data.SqlTypes.SqlStreamChars.Write Method</span></span>](system.data.sqltypes.sqlstreamchars.write.md)
* [<span data-ttu-id="d7c96-136">System. ıO. MemoryStream. ınternalgetoriginandlength yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7c96-136">System.IO.MemoryStream.InternalGetOriginAndLength Method</span></span>](system.io.memorystream.internalgetoriginandlength.md)
* [<span data-ttu-id="d7c96-137">System .net. Connection sınıfı</span><span class="sxs-lookup"><span data-stu-id="d7c96-137">System.Net.Connection Class</span></span>](connection.md)
* [<span data-ttu-id="d7c96-138">System .net. Connection. d\_WriteList alanı</span><span class="sxs-lookup"><span data-stu-id="d7c96-138">System.Net.Connection.m\_WriteList Field</span></span>](m_writelist.md)
* [<span data-ttu-id="d7c96-139">System .net. ConnectionGroup sınıfı</span><span class="sxs-lookup"><span data-stu-id="d7c96-139">System.Net.ConnectionGroup Class</span></span>](connectiongroup.md)
* [<span data-ttu-id="d7c96-140">System .net. ConnectionGroup. d\_ConnectionList alanı</span><span class="sxs-lookup"><span data-stu-id="d7c96-140">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](m_connectionlist.md)
* [<span data-ttu-id="d7c96-141">System .net. ConnectStream. Connection özelliği</span><span class="sxs-lookup"><span data-stu-id="d7c96-141">System.Net.ConnectStream.Connection Property</span></span>](system.net.connectstream.connection.md)
* [<span data-ttu-id="d7c96-142">System .net. CoreResponseData sınıfı</span><span class="sxs-lookup"><span data-stu-id="d7c96-142">System.Net.CoreResponseData Class</span></span>](coreresponsedata.md)
* [<span data-ttu-id="d7c96-143">System .net. CoreResponseData. d\_ResponseHeaders alanı</span><span class="sxs-lookup"><span data-stu-id="d7c96-143">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](coreresponsedata_m_responseheaders.md)
* [<span data-ttu-id="d7c96-144">System .net. CoreResponseData. d\_StatusCode alanı</span><span class="sxs-lookup"><span data-stu-id="d7c96-144">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](coreresponsedata_m_statuscode.md)
* [<span data-ttu-id="d7c96-145">System .net. HttpWebRequest.\_oto yeniden yönlendirme alanı</span><span class="sxs-lookup"><span data-stu-id="d7c96-145">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](_autoredirects.md)
* [<span data-ttu-id="d7c96-146">System .net. HttpWebRequest.\_CoreResponse alanı</span><span class="sxs-lookup"><span data-stu-id="d7c96-146">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](httpwebrequest__coreresponse.md)
* [<span data-ttu-id="d7c96-147">System .net. HttpWebRequest.\_HttpResponse alanı</span><span class="sxs-lookup"><span data-stu-id="d7c96-147">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](_httpresponse.md)
* [<span data-ttu-id="d7c96-148">System .net. PooledStream. NetworkStream özelliği</span><span class="sxs-lookup"><span data-stu-id="d7c96-148">System.Net.PooledStream.NetworkStream Property</span></span>](system.net.pooledstream.networkstream.md)
* [<span data-ttu-id="d7c96-149">System .net. RtcState sınıfı</span><span class="sxs-lookup"><span data-stu-id="d7c96-149">System.Net.RtcState class</span></span>](system.net.rtcstate.md)
* [<span data-ttu-id="d7c96-150">System .net. ServicePoint. d\_ConnectionGroupList alanı</span><span class="sxs-lookup"><span data-stu-id="d7c96-150">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](m_connectiongrouplist.md)
* [<span data-ttu-id="d7c96-151">System .net. ServicePointManager. s\_ServicePointTable alanı</span><span class="sxs-lookup"><span data-stu-id="d7c96-151">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](s_servicepointtable.md)
* [<span data-ttu-id="d7c96-152">System .net. TlsStream. m_Worker alanı</span><span class="sxs-lookup"><span data-stu-id="d7c96-152">System.Net.TlsStream.m_Worker Field</span></span>](system.net.tlsstream.m_worker.md)
* [<span data-ttu-id="d7c96-153">System .net. Security. SslState. SslProtocol özelliği</span><span class="sxs-lookup"><span data-stu-id="d7c96-153">System.Net.Security.SslState.SslProtocol Property</span></span>](system.net.security.sslstate.sslprotocol.md)
* [<span data-ttu-id="d7c96-154">System. ServiceModel. Channels. Message. BodyToString yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7c96-154">System.ServiceModel.Channels.Message.BodyToString Method</span></span>](system.servicemodel.channels.message.bodytostring.md)
* [<span data-ttu-id="d7c96-155">System. ServiceModel. Channels. Message. WriteStartHeaders yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7c96-155">System.ServiceModel.Channels.Message.WriteStartHeaders Method</span></span>](system.servicemodel.channels.message.writestartheaders.md)
* [<span data-ttu-id="d7c96-156">System. Windows. Diagnostics. VisualDiagnostics. s\_ıdebuggercheckdisabledfortestamaçlar alanı</span><span class="sxs-lookup"><span data-stu-id="d7c96-156">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [<span data-ttu-id="d7c96-157">System. Windows. Forms. Design. DataMemberFieldEditor sınıfı</span><span class="sxs-lookup"><span data-stu-id="d7c96-157">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](datamemberfieldeditor-class.md)
* [<span data-ttu-id="d7c96-158">System. Windows. Forms. Design. Datamemberlistedıtor sınıfı</span><span class="sxs-lookup"><span data-stu-id="d7c96-158">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](datamemberlisteditor-class.md)
* [<span data-ttu-id="d7c96-159">System. xml. XmlReader. CreateSqlReader yöntemi</span><span class="sxs-lookup"><span data-stu-id="d7c96-159">System.Xml.XmlReader.CreateSqlReader Method</span></span>](system.xml.xmlreader.createsqlreader.md)
* [<span data-ttu-id="d7c96-160">ADODB. Bağlantı arabirimi</span><span class="sxs-lookup"><span data-stu-id="d7c96-160">adodb.Connection Interface</span></span>](adodb.connection.md)
* [<span data-ttu-id="d7c96-161">ADODB. EventReason sabit listesi</span><span class="sxs-lookup"><span data-stu-id="d7c96-161">adodb.EventReason Enum</span></span>](adodb.eventreasonenum.md)
* [<span data-ttu-id="d7c96-162">ADODB. EventStatus numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d7c96-162">adodb.EventStatus Enum</span></span>](adodb.eventstatusenum.md)
* [<span data-ttu-id="d7c96-163">Stdole. DISPPARAMS yapısı</span><span class="sxs-lookup"><span data-stu-id="d7c96-163">stdole.DISPPARAMS Structure</span></span>](stdole.dispparams.md)
* [<span data-ttu-id="d7c96-164">Stdole. EXCEPıNFO yapısı</span><span class="sxs-lookup"><span data-stu-id="d7c96-164">stdole.EXCEPINFO Structure</span></span>](stdole.excepinfo.md)
* [<span data-ttu-id="d7c96-165">Stdole. IFont.Name özelliği</span><span class="sxs-lookup"><span data-stu-id="d7c96-165">stdole.IFont.Name Property</span></span>](stdole.ifont.name.md)
* [<span data-ttu-id="d7c96-166">Stdole. IFontDisp arabirimi</span><span class="sxs-lookup"><span data-stu-id="d7c96-166">stdole.IFontDisp Interface</span></span>](stdole.ifontdisp.md)
* [<span data-ttu-id="d7c96-167">Stdole. Ipıture. Handle özelliği</span><span class="sxs-lookup"><span data-stu-id="d7c96-167">stdole.IPicture.Handle Property</span></span>](stdole.ipicture.handle.md)
* [<span data-ttu-id="d7c96-168">Stdole. IPictureDisp. Handle özelliği</span><span class="sxs-lookup"><span data-stu-id="d7c96-168">stdole.IPictureDisp.Handle Property</span></span>](stdole.ipicturedisp.handle.md)
* [<span data-ttu-id="d7c96-169">Stdole. StdFont arabirimi</span><span class="sxs-lookup"><span data-stu-id="d7c96-169">stdole.StdFont Interface</span></span>](stdole.stdfont.md)
* [<span data-ttu-id="d7c96-170">Stdole. StdPicture arabirimi</span><span class="sxs-lookup"><span data-stu-id="d7c96-170">stdole.StdPicture Interface</span></span>](stdole.stdpicture.md)
  
## <a name="see-also"></a><span data-ttu-id="d7c96-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7c96-171">See also</span></span>

* [<span data-ttu-id="d7c96-172">.NET Framework ve Bant Dışı Yayınlar</span><span class="sxs-lookup"><span data-stu-id="d7c96-172">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
