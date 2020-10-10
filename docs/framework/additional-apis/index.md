---
title: Ek sınıf kitaplıkları ve API'ler
description: Bant dışı (OOB) projeler, platforma özgü kitaplıklar ve özel API 'Ler dahil olmak üzere .NET 'teki ek sınıf kitaplıklarını ve API 'Leri inceleyin.
ms.date: 08/11/2020
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
ms.topic: conceptual
ms.openlocfilehash: 55cb37cc2c9184eeb55ee0aab39e97f4a3f7b7d8
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877645"
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="16b6a-103">Ek sınıf kitaplıkları ve API'ler</span><span class="sxs-lookup"><span data-stu-id="16b6a-103">Additional class libraries and APIs</span></span>

<span data-ttu-id="16b6a-104">Bu makalede, bant dışında yayınlanan, belirli bir platformu hedefleyen veya özel ya da iç türler olan .NET Framework API 'Ler listelenir.</span><span class="sxs-lookup"><span data-stu-id="16b6a-104">This article lists .NET Framework APIs that either were released out of band, target a specific platform, or are private or internal types.</span></span>

## <a name="oob-projects"></a><span data-ttu-id="16b6a-105">OOB projeleri</span><span class="sxs-lookup"><span data-stu-id="16b6a-105">OOB projects</span></span>

<span data-ttu-id="16b6a-106">Platformlar arası geliştirmeyi artırmak ve yeni işlevsellik sunmak için bazı .NET Framework Özellikler bant dışı (OOB) serbest bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="16b6a-106">To improve cross-platform development and introduce new functionality early, some .NET Framework features were released out of band (OOB).</span></span>

| <span data-ttu-id="16b6a-107">Proje</span><span class="sxs-lookup"><span data-stu-id="16b6a-107">Project</span></span> | <span data-ttu-id="16b6a-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16b6a-108">Description</span></span> |
| ------- | ----------- |
| <xref:System.Collections.Immutable> | <span data-ttu-id="16b6a-109">, İş parçacığı açısından güvenli olan ve içeriklerinin hiçbir şekilde değişmeme garantisi sağlayan koleksiyonlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="16b6a-109">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="16b6a-110"><xref:System.Net.Http.HttpClient>Windows 'un WinHTTP arabirimine dayalı olarak bir ileti işleyicisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="16b6a-110">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="16b6a-111">SıMD donanım tabanlı hızlandırmasının avantajlarından yararlanan bir vektör türleri kitaplığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="16b6a-111">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>|
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="16b6a-112">TPL veri akışı kitaplığı, eşzamanlılık özellikli uygulamaların sağlamlığını artırmaya yardımcı olmak için veri akışı bileşenleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="16b6a-112">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |

## <a name="platform-specific-libraries"></a><span data-ttu-id="16b6a-113">Platforma özgü kitaplıklar</span><span class="sxs-lookup"><span data-stu-id="16b6a-113">Platform-specific libraries</span></span>

<span data-ttu-id="16b6a-114">Bazı kitaplıklar belirli platformları hedeflemelidir.</span><span class="sxs-lookup"><span data-stu-id="16b6a-114">Some libraries target specific platforms.</span></span> <span data-ttu-id="16b6a-115">Örneğin, <xref:System.Text.CodePagesEncodingProvider> sınıfı kod sayfası kodlamalarını .NET Framework kullanılarak GELIŞTIRILEN UWP uygulamaları için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="16b6a-115">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using .NET Framework.</span></span>

| <span data-ttu-id="16b6a-116">Proje</span><span class="sxs-lookup"><span data-stu-id="16b6a-116">Project</span></span> | <span data-ttu-id="16b6a-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16b6a-117">Description</span></span> |
| ------- | ----------- |
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="16b6a-118"><xref:System.Text.EncodingProvider>Kod sayfası kodlamalarını Evrensel Windows platformu hedefleyen uygulamalar için kullanılabilir hale getirmek için sınıfını genişletir.</span><span class="sxs-lookup"><span data-stu-id="16b6a-118">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |

## <a name="private-apis"></a><span data-ttu-id="16b6a-119">Özel API 'Ler</span><span class="sxs-lookup"><span data-stu-id="16b6a-119">Private APIs</span></span>

<span data-ttu-id="16b6a-120">Bu API 'Ler ürün altyapısını destekler ve doğrudan kodunuzdan kullanılmak üzere tasarlanmamıştır veya desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="16b6a-120">These APIs support the product infrastructure and are not intended or supported to be used directly from your code.</span></span>

* [<span data-ttu-id="16b6a-121">Microsoft. SqlServer. Server. Smorderproperty. Item özelliği</span><span class="sxs-lookup"><span data-stu-id="16b6a-121">Microsoft.SqlServer.Server.SmiOrderProperty.Item property</span></span>](microsoft.sqlserver.server.smiorderproperty.item.md)
* [<span data-ttu-id="16b6a-122">System. Exception. PrepForRemoting yöntemi</span><span class="sxs-lookup"><span data-stu-id="16b6a-122">System.Exception.PrepForRemoting method</span></span>](system.exception.prepforremoting.md)
* [<span data-ttu-id="16b6a-123">System. Data. SqlTypes. SqlChars. Stream özelliği</span><span class="sxs-lookup"><span data-stu-id="16b6a-123">System.Data.SqlTypes.SqlChars.Stream property</span></span>](system.data.sqltypes.sqlchars.stream.md)
* [<span data-ttu-id="16b6a-124">System. Data. SqlTypes. SqlStreamChars Oluşturucusu</span><span class="sxs-lookup"><span data-stu-id="16b6a-124">System.Data.SqlTypes.SqlStreamChars Constructor</span></span>](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [<span data-ttu-id="16b6a-125">System. Data. SqlTypes. SqlStreamChars. CanSeek özelliği</span><span class="sxs-lookup"><span data-stu-id="16b6a-125">System.Data.SqlTypes.SqlStreamChars.CanSeek property</span></span>](system.data.sqltypes.sqlstreamchars.canseek.md)
* [<span data-ttu-id="16b6a-126">System. Data. SqlTypes. SqlStreamChars. IsNull Özelliği</span><span class="sxs-lookup"><span data-stu-id="16b6a-126">System.Data.SqlTypes.SqlStreamChars.IsNull property</span></span>](system.data.sqltypes.sqlstreamchars.isnull.md)
* [<span data-ttu-id="16b6a-127">System. Data. SqlTypes. SqlStreamChars. length özelliği</span><span class="sxs-lookup"><span data-stu-id="16b6a-127">System.Data.SqlTypes.SqlStreamChars.Length property</span></span>](system.data.sqltypes.sqlstreamchars.length.md)
* [<span data-ttu-id="16b6a-128">System. Data. SqlTypes. SqlStreamChars. Close yöntemi</span><span class="sxs-lookup"><span data-stu-id="16b6a-128">System.Data.SqlTypes.SqlStreamChars.Close method</span></span>](system.data.sqltypes.sqlstreamchars.close.md)
* [<span data-ttu-id="16b6a-129">System. Data. SqlTypes. SqlStreamChars. Dispose yöntemi</span><span class="sxs-lookup"><span data-stu-id="16b6a-129">System.Data.SqlTypes.SqlStreamChars.Dispose method</span></span>](system.data.sqltypes.sqlstreamchars.dispose.md)
* [<span data-ttu-id="16b6a-130">System. Data. SqlTypes. SqlStreamChars. Flush yöntemi</span><span class="sxs-lookup"><span data-stu-id="16b6a-130">System.Data.SqlTypes.SqlStreamChars.Flush method</span></span>](system.data.sqltypes.sqlstreamchars.flush.md)
* [<span data-ttu-id="16b6a-131">System. Data. SqlTypes. SqlStreamChars. Read yöntemi</span><span class="sxs-lookup"><span data-stu-id="16b6a-131">System.Data.SqlTypes.SqlStreamChars.Read method</span></span>](system.data.sqltypes.sqlstreamchars.read.md)
* [<span data-ttu-id="16b6a-132">System. Data. SqlTypes. SqlStreamChars. Seek yöntemi</span><span class="sxs-lookup"><span data-stu-id="16b6a-132">System.Data.SqlTypes.SqlStreamChars.Seek method</span></span>](system.data.sqltypes.sqlstreamchars.seek.md)
* [<span data-ttu-id="16b6a-133">System. Data. SqlTypes. SqlStreamChars. SetLength yöntemi</span><span class="sxs-lookup"><span data-stu-id="16b6a-133">System.Data.SqlTypes.SqlStreamChars.SetLength method</span></span>](system.data.sqltypes.sqlstreamchars.setlength.md)
* [<span data-ttu-id="16b6a-134">System. Data. SqlTypes. SqlStreamChars. Write yöntemi</span><span class="sxs-lookup"><span data-stu-id="16b6a-134">System.Data.SqlTypes.SqlStreamChars.Write method</span></span>](system.data.sqltypes.sqlstreamchars.write.md)
* [<span data-ttu-id="16b6a-135">System. ıO. MemoryStream. ınternalgetoriginandlength yöntemi</span><span class="sxs-lookup"><span data-stu-id="16b6a-135">System.IO.MemoryStream.InternalGetOriginAndLength method</span></span>](system.io.memorystream.internalgetoriginandlength.md)
* [<span data-ttu-id="16b6a-136">System .net. ComNetOS sınıfı</span><span class="sxs-lookup"><span data-stu-id="16b6a-136">System.Net.ComNetOS class</span></span>](system.net.comnetos.md)
* [<span data-ttu-id="16b6a-137">System .net. Connection sınıfı</span><span class="sxs-lookup"><span data-stu-id="16b6a-137">System.Net.Connection class</span></span>](connection.md)
* [<span data-ttu-id="16b6a-138">System .net. Connection. d \_ writelist alanı</span><span class="sxs-lookup"><span data-stu-id="16b6a-138">System.Net.Connection.m\_WriteList field</span></span>](m_writelist.md)
* [<span data-ttu-id="16b6a-139">System .net. ConnectionGroup sınıfı</span><span class="sxs-lookup"><span data-stu-id="16b6a-139">System.Net.ConnectionGroup class</span></span>](connectiongroup.md)
* [<span data-ttu-id="16b6a-140">System .net. ConnectionGroup. d \_ connectionlist alanı</span><span class="sxs-lookup"><span data-stu-id="16b6a-140">System.Net.ConnectionGroup.m\_ConnectionList field</span></span>](m_connectionlist.md)
* [<span data-ttu-id="16b6a-141">System .net. ConnectStream. Connection özelliği</span><span class="sxs-lookup"><span data-stu-id="16b6a-141">System.Net.ConnectStream.Connection property</span></span>](system.net.connectstream.connection.md)
* [<span data-ttu-id="16b6a-142">System .net. CoreResponseData sınıfı</span><span class="sxs-lookup"><span data-stu-id="16b6a-142">System.Net.CoreResponseData class</span></span>](coreresponsedata.md)
* [<span data-ttu-id="16b6a-143">System .net. CoreResponseData. d \_ ResponseHeaders alanı</span><span class="sxs-lookup"><span data-stu-id="16b6a-143">System.Net.CoreResponseData.m\_ResponseHeaders field</span></span>](coreresponsedata_m_responseheaders.md)
* [<span data-ttu-id="16b6a-144">System .net. CoreResponseData. \_ mstatuscode alanı</span><span class="sxs-lookup"><span data-stu-id="16b6a-144">System.Net.CoreResponseData.m\_StatusCode field</span></span>](coreresponsedata_m_statuscode.md)
* [<span data-ttu-id="16b6a-145">System .net. ExceptionHelper sınıfı</span><span class="sxs-lookup"><span data-stu-id="16b6a-145">System.Net.ExceptionHelper class</span></span>](system.net.exceptionhelper.md)
* [<span data-ttu-id="16b6a-146">System .net. HttpStatusDescription sınıfı</span><span class="sxs-lookup"><span data-stu-id="16b6a-146">System.Net.HttpStatusDescription class</span></span>](system.net.httpstatusdescription.md)
* [<span data-ttu-id="16b6a-147">Sistem .net. HttpWebRequest. \_ Oto yeniden yönlendirmeler alanı</span><span class="sxs-lookup"><span data-stu-id="16b6a-147">System.Net.HttpWebRequest.\_AutoRedirects field</span></span>](_autoredirects.md)
* [<span data-ttu-id="16b6a-148">Sistem .net. HttpWebRequest. \_ CoreResponse alanı</span><span class="sxs-lookup"><span data-stu-id="16b6a-148">System.Net.HttpWebRequest.\_CoreResponse field</span></span>](httpwebrequest__coreresponse.md)
* [<span data-ttu-id="16b6a-149">Sistem .net. HttpWebRequest. \_ HttpResponse alanı</span><span class="sxs-lookup"><span data-stu-id="16b6a-149">System.Net.HttpWebRequest.\_HttpResponse field</span></span>](_httpresponse.md)
* [<span data-ttu-id="16b6a-150">System .net. Logging sınıfı</span><span class="sxs-lookup"><span data-stu-id="16b6a-150">System.Net.Logging class</span></span>](system.net.logging.md)
* [<span data-ttu-id="16b6a-151">System .net. mail. MailAddressParser sınıfı</span><span class="sxs-lookup"><span data-stu-id="16b6a-151">System.Net.Mail.MailAddressParser class</span></span>](system.net.mail.mailaddressparser.md)
* [<span data-ttu-id="16b6a-152">System .net. mail. QuotedPairReader sınıfı</span><span class="sxs-lookup"><span data-stu-id="16b6a-152">System.Net.Mail.QuotedPairReader class</span></span>](system.net.mail.quotedpairreader.md)
* [<span data-ttu-id="16b6a-153">System .net. MIME. MailBnfHelper sınıfı</span><span class="sxs-lookup"><span data-stu-id="16b6a-153">System.Net.Mime.MailBnfHelper class</span></span>](system.net.mime.mailbnfhelper.md)
* [<span data-ttu-id="16b6a-154">System .net. PooledStream. NetworkStream özelliği</span><span class="sxs-lookup"><span data-stu-id="16b6a-154">System.Net.PooledStream.NetworkStream property</span></span>](system.net.pooledstream.networkstream.md)
* [<span data-ttu-id="16b6a-155">System .net. RtcState sınıfı</span><span class="sxs-lookup"><span data-stu-id="16b6a-155">System.Net.RtcState class</span></span>](system.net.rtcstate.md)
* [<span data-ttu-id="16b6a-156">System .net. Security. SslState. SslProtocol özelliği</span><span class="sxs-lookup"><span data-stu-id="16b6a-156">System.Net.Security.SslState.SslProtocol property</span></span>](system.net.security.sslstate.sslprotocol.md)
* [<span data-ttu-id="16b6a-157">System .net. ServicePoint. d \_ connectiongrouplist alanı</span><span class="sxs-lookup"><span data-stu-id="16b6a-157">System.Net.ServicePoint.m\_ConnectionGroupList field</span></span>](m_connectiongrouplist.md)
* [<span data-ttu-id="16b6a-158">System .net. ServicePointManager. CloseConnectionGroups yöntemi</span><span class="sxs-lookup"><span data-stu-id="16b6a-158">System.Net.ServicePointManager.CloseConnectionGroups method</span></span>](system.net.servicepointmanager.closeconnectiongroups.md)
* [<span data-ttu-id="16b6a-159">System .net. ServicePointManager. s \_ servicepointtable alanı</span><span class="sxs-lookup"><span data-stu-id="16b6a-159">System.Net.ServicePointManager.s\_ServicePointTable field</span></span>](s_servicepointtable.md)
* [<span data-ttu-id="16b6a-160">System.Net.TlsStream.m_Worker alanı</span><span class="sxs-lookup"><span data-stu-id="16b6a-160">System.Net.TlsStream.m_Worker field</span></span>](system.net.tlsstream.m_worker.md)
* [<span data-ttu-id="16b6a-161">System .net. UnsafeNclNativeMethods sınıfı</span><span class="sxs-lookup"><span data-stu-id="16b6a-161">System.Net.UnsafeNclNativeMethods class</span></span>](system.net.unsafenclnativemethods.md)
* [<span data-ttu-id="16b6a-162">System .net. WebHeaderCollection. Addınternal yöntemi</span><span class="sxs-lookup"><span data-stu-id="16b6a-162">System.Net.WebHeaderCollection.AddInternal method</span></span>](system.net.webheadercollection.addinternal.md)
* [<span data-ttu-id="16b6a-163">System. ServiceModel. Channels. Message. BodyToString yöntemi</span><span class="sxs-lookup"><span data-stu-id="16b6a-163">System.ServiceModel.Channels.Message.BodyToString method</span></span>](system.servicemodel.channels.message.bodytostring.md)
* [<span data-ttu-id="16b6a-164">System. ServiceModel. Channels. Message. WriteStartHeaders yöntemi</span><span class="sxs-lookup"><span data-stu-id="16b6a-164">System.ServiceModel.Channels.Message.WriteStartHeaders method</span></span>](system.servicemodel.channels.message.writestartheaders.md)
* [<span data-ttu-id="16b6a-165">System. Web. Compilation. Controlbuilderyakalayıcısı sınıfı</span><span class="sxs-lookup"><span data-stu-id="16b6a-165">System.Web.Compilation.ControlBuilderInterceptor class</span></span>](controlbuilderinterceptor-class.md)
* [<span data-ttu-id="16b6a-166">System. Windows. Controls. Gridviewwheaderrowpresenter. FindHeaderByColumn yöntemi</span><span class="sxs-lookup"><span data-stu-id="16b6a-166">System.Windows.Controls.GridViewHeaderRowPresenter.FindHeaderByColumn method</span></span>](system.windows.controls.gridviewheaderrowpresenter.findheaderbycolumn.md)
* [<span data-ttu-id="16b6a-167">System. Windows. Controls. GridViewHeaderRowPresenter. MakeParentItemsControlGotFocus yöntemi</span><span class="sxs-lookup"><span data-stu-id="16b6a-167">System.Windows.Controls.GridViewHeaderRowPresenter.MakeParentItemsControlGotFocus method</span></span>](system.windows.controls.gridviewheaderrowpresenter.makeparentitemscontrolgotfocus.md)
* [<span data-ttu-id="16b6a-168">System. Windows. Controls. Gridviewwheaderrowpresenter. PrepareHeaderDrag yöntemi</span><span class="sxs-lookup"><span data-stu-id="16b6a-168">System.Windows.Controls.GridViewHeaderRowPresenter.PrepareHeaderDrag method</span></span>](system.windows.controls.gridviewheaderrowpresenter.prepareheaderdrag.md)
* [<span data-ttu-id="16b6a-169">System. Windows. Diagnostics. VisualDiagnostics. s \_ ıdebuggercheckdisabledfortestamaçlar alanı</span><span class="sxs-lookup"><span data-stu-id="16b6a-169">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes field</span></span>](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [<span data-ttu-id="16b6a-170">System. Windows. Forms. Design. DataMemberFieldEditor sınıfı</span><span class="sxs-lookup"><span data-stu-id="16b6a-170">System.Windows.Forms.Design.DataMemberFieldEditor class</span></span>](datamemberfieldeditor-class.md)
* [<span data-ttu-id="16b6a-171">System. Windows. Forms. Design. Datamemberlistedıtor sınıfı</span><span class="sxs-lookup"><span data-stu-id="16b6a-171">System.Windows.Forms.Design.DataMemberListEditor class</span></span>](datamemberlisteditor-class.md)
* [<span data-ttu-id="16b6a-172">System.Xml.XmlReader. CreateSqlReader yöntemi</span><span class="sxs-lookup"><span data-stu-id="16b6a-172">System.Xml.XmlReader.CreateSqlReader method</span></span>](system.xml.xmlreader.createsqlreader.md)
* [<span data-ttu-id="16b6a-173">ADODB. Bağlantı arabirimi</span><span class="sxs-lookup"><span data-stu-id="16b6a-173">adodb.Connection interface</span></span>](adodb.connection.md)
* [<span data-ttu-id="16b6a-174">ADODB. EventReason sabit listesi</span><span class="sxs-lookup"><span data-stu-id="16b6a-174">adodb.EventReason enum</span></span>](adodb.eventreasonenum.md)
* [<span data-ttu-id="16b6a-175">ADODB. EventStatus numaralandırması</span><span class="sxs-lookup"><span data-stu-id="16b6a-175">adodb.EventStatus enum</span></span>](adodb.eventstatusenum.md)
* [<span data-ttu-id="16b6a-176">Stdole. DISPPARAMS yapısı</span><span class="sxs-lookup"><span data-stu-id="16b6a-176">stdole.DISPPARAMS Structure</span></span>](stdole.dispparams.md)
* [<span data-ttu-id="16b6a-177">Stdole. EXCEPıNFO yapısı</span><span class="sxs-lookup"><span data-stu-id="16b6a-177">stdole.EXCEPINFO Structure</span></span>](stdole.excepinfo.md)
* [<span data-ttu-id="16b6a-178">Stdole. IFont.Name özelliği</span><span class="sxs-lookup"><span data-stu-id="16b6a-178">stdole.IFont.Name property</span></span>](stdole.ifont.name.md)
* [<span data-ttu-id="16b6a-179">Stdole. IFontDisp arabirimi</span><span class="sxs-lookup"><span data-stu-id="16b6a-179">stdole.IFontDisp interface</span></span>](stdole.ifontdisp.md)
* [<span data-ttu-id="16b6a-180">Stdole. Ipıture. Handle özelliği</span><span class="sxs-lookup"><span data-stu-id="16b6a-180">stdole.IPicture.Handle property</span></span>](stdole.ipicture.handle.md)
* [<span data-ttu-id="16b6a-181">Stdole. IPictureDisp. Handle özelliği</span><span class="sxs-lookup"><span data-stu-id="16b6a-181">stdole.IPictureDisp.Handle property</span></span>](stdole.ipicturedisp.handle.md)
* [<span data-ttu-id="16b6a-182">Stdole. StdFont arabirimi</span><span class="sxs-lookup"><span data-stu-id="16b6a-182">stdole.StdFont interface</span></span>](stdole.stdfont.md)
* [<span data-ttu-id="16b6a-183">Stdole. StdPicture arabirimi</span><span class="sxs-lookup"><span data-stu-id="16b6a-183">stdole.StdPicture interface</span></span>](stdole.stdpicture.md)

## <a name="see-also"></a><span data-ttu-id="16b6a-184">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16b6a-184">See also</span></span>

* [<span data-ttu-id="16b6a-185">.NET Framework ve bant dışı yayınlar</span><span class="sxs-lookup"><span data-stu-id="16b6a-185">.NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
