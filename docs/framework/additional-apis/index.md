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
ms.openlocfilehash: c6404df5d4f0be381bc0a9c1924fcf82cf078306
ms.sourcegitcommit: 70d6a7e4f7187cbfa332f0f8be76566f7828cfcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88075481"
---
# <a name="additional-class-libraries-and-apis"></a>Ek sınıf kitaplıkları ve API'ler

Bu makalede, bant dışında yayınlanan, belirli bir platformu hedefleyen veya özel ya da iç türler olan .NET Framework API 'Ler listelenir.

## <a name="oob-projects"></a>OOB projeleri

Platformlar arası geliştirmeyi artırmak ve yeni işlevsellik sunmak için bazı .NET Framework Özellikler bant dışı (OOB) serbest bırakıldı.

| Proje | Açıklama |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | , İş parçacığı açısından güvenli olan ve içeriklerinin hiçbir şekilde değişmeme garantisi sağlayan koleksiyonlar sağlar. |
| <xref:System.Net.Http.WinHttpHandler> | <xref:System.Net.Http.HttpClient>Windows 'un WinHTTP arabirimine dayalı olarak bir ileti işleyicisi sağlar. |
| <xref:System.Numerics> | SıMD donanım tabanlı hızlandırmasının avantajlarından yararlanan bir vektör türleri kitaplığı sağlar.|
| <xref:System.Threading.Tasks.Dataflow> | TPL veri akışı kitaplığı, eşzamanlılık özellikli uygulamaların sağlamlığını artırmaya yardımcı olmak için veri akışı bileşenleri sağlar. |  

## <a name="platform-specific-libraries"></a>Platforma özgü kitaplıklar

Bazı kitaplıklar belirli platformları hedeflemelidir. Örneğin, <xref:System.Text.CodePagesEncodingProvider> sınıfı kod sayfası kodlamalarını .NET Framework kullanılarak GELIŞTIRILEN UWP uygulamaları için kullanılabilir hale getirir.
  
| Proje | Açıklama |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <xref:System.Text.EncodingProvider>Kod sayfası kodlamalarını Evrensel Windows platformu hedefleyen uygulamalar için kullanılabilir hale getirmek için sınıfını genişletir. |  
  
## <a name="private-apis"></a>Özel API 'Ler  

Bu API 'Ler ürün altyapısını destekler ve doğrudan kodunuzdan kullanılmak üzere tasarlanmamıştır veya desteklenmez.  
  
* [Microsoft. SqlServer. Server. Smorderproperty. Item özelliği](microsoft.sqlserver.server.smiorderproperty.item.md)
* [System. Exception. PrepForRemoting yöntemi](system.exception.prepforremoting.md)
* [System. Data. SqlTypes. SqlChars. Stream özelliği](system.data.sqltypes.sqlchars.stream.md)
* [System. Data. SqlTypes. SqlStreamChars Oluşturucusu](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [System. Data. SqlTypes. SqlStreamChars. CanSeek özelliği](system.data.sqltypes.sqlstreamchars.canseek.md)
* [System. Data. SqlTypes. SqlStreamChars. IsNull Özelliği](system.data.sqltypes.sqlstreamchars.isnull.md)
* [System. Data. SqlTypes. SqlStreamChars. length özelliği](system.data.sqltypes.sqlstreamchars.length.md)
* [System. Data. SqlTypes. SqlStreamChars. Close yöntemi](system.data.sqltypes.sqlstreamchars.close.md)
* [System. Data. SqlTypes. SqlStreamChars. Dispose yöntemi](system.data.sqltypes.sqlstreamchars.dispose.md)
* [System. Data. SqlTypes. SqlStreamChars. Flush yöntemi](system.data.sqltypes.sqlstreamchars.flush.md)
* [System. Data. SqlTypes. SqlStreamChars. Read yöntemi](system.data.sqltypes.sqlstreamchars.read.md)
* [System. Data. SqlTypes. SqlStreamChars. Seek yöntemi](system.data.sqltypes.sqlstreamchars.seek.md)
* [System. Data. SqlTypes. SqlStreamChars. SetLength yöntemi](system.data.sqltypes.sqlstreamchars.setlength.md)
* [System. Data. SqlTypes. SqlStreamChars. Write yöntemi](system.data.sqltypes.sqlstreamchars.write.md)
* [System. ıO. MemoryStream. ınternalgetoriginandlength yöntemi](system.io.memorystream.internalgetoriginandlength.md)
* [System .net. ComNetOS sınıfı](system.net.comnetos.md)
* [System .net. Connection sınıfı](connection.md)
* [System .net. Connection. d \_ writelist alanı](m_writelist.md)
* [System .net. ConnectionGroup sınıfı](connectiongroup.md)
* [System .net. ConnectionGroup. d \_ connectionlist alanı](m_connectionlist.md)
* [System .net. ConnectStream. Connection özelliği](system.net.connectstream.connection.md)
* [System .net. CoreResponseData sınıfı](coreresponsedata.md)
* [System .net. CoreResponseData. d \_ ResponseHeaders alanı](coreresponsedata_m_responseheaders.md)
* [System .net. CoreResponseData. \_ mstatuscode alanı](coreresponsedata_m_statuscode.md)
* [System .net. ExceptionHelper sınıfı](system.net.exceptionhelper.md)
* [System .net. HttpStatusDescription sınıfı](system.net.httpstatusdescription.md)
* [Sistem .net. HttpWebRequest. \_ Oto yeniden yönlendirmeler alanı](_autoredirects.md)
* [Sistem .net. HttpWebRequest. \_ CoreResponse alanı](httpwebrequest__coreresponse.md)
* [Sistem .net. HttpWebRequest. \_ HttpResponse alanı](_httpresponse.md)
* [System .net. Logging sınıfı](system.net.logging.md)
* [System .net. mail. MailAddressParser sınıfı](system.net.mail.mailaddressparser.md)
* [System .net. mail. QuotedPairReader sınıfı](system.net.mail.quotedpairreader.md)
* [System .net. MIME. MailBnfHelper sınıfı](system.net.mime.mailbnfhelper.md)
* [System .net. PooledStream. NetworkStream özelliği](system.net.pooledstream.networkstream.md)
* [System .net. RtcState sınıfı](system.net.rtcstate.md)
* [System .net. Security. SslState. SslProtocol özelliği](system.net.security.sslstate.sslprotocol.md)
* [System .net. ServicePoint. d \_ connectiongrouplist alanı](m_connectiongrouplist.md)
* [System .net. ServicePointManager. CloseConnectionGroups yöntemi](system.net.servicepointmanager.closeconnectiongroups.md)
* [System .net. ServicePointManager. s \_ servicepointtable alanı](s_servicepointtable.md)
* [System .net. TlsStream. m_Worker alanı](system.net.tlsstream.m_worker.md)
* [System .net. UnsafeNclNativeMethods sınıfı](system.net.unsafenclnativemethods.md)
* [System .net. WebHeaderCollection. Addınternal yöntemi](system.net.webheadercollection.addinternal.md)
* [System. ServiceModel. Channels. Message. BodyToString yöntemi](system.servicemodel.channels.message.bodytostring.md)
* [System. ServiceModel. Channels. Message. WriteStartHeaders yöntemi](system.servicemodel.channels.message.writestartheaders.md)
* [System. Web. Compilation. Controlbuilderyakalayıcısı sınıfı](controlbuilderinterceptor-class.md)
* [System. Windows. Diagnostics. VisualDiagnostics. s \_ ıdebuggercheckdisabledfortestamaçlar alanı](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [System. Windows. Forms. Design. DataMemberFieldEditor sınıfı](datamemberfieldeditor-class.md)
* [System. Windows. Forms. Design. Datamemberlistedıtor sınıfı](datamemberlisteditor-class.md)
* [System.Xml.XmlReader. CreateSqlReader yöntemi](system.xml.xmlreader.createsqlreader.md)
* [ADODB. Bağlantı arabirimi](adodb.connection.md)
* [ADODB. EventReason sabit listesi](adodb.eventreasonenum.md)
* [ADODB. EventStatus numaralandırması](adodb.eventstatusenum.md)
* [Stdole. DISPPARAMS yapısı](stdole.dispparams.md)
* [Stdole. EXCEPıNFO yapısı](stdole.excepinfo.md)
* [Stdole. IFont.Name özelliği](stdole.ifont.name.md)
* [Stdole. IFontDisp arabirimi](stdole.ifontdisp.md)
* [Stdole. Ipıture. Handle özelliği](stdole.ipicture.handle.md)
* [Stdole. IPictureDisp. Handle özelliği](stdole.ipicturedisp.handle.md)
* [Stdole. StdFont arabirimi](stdole.stdfont.md)
* [Stdole. StdPicture arabirimi](stdole.stdpicture.md)
  
## <a name="see-also"></a>Ayrıca bkz.

* [.NET Framework ve bant dışı yayınlar](../get-started/the-net-framework-and-out-of-band-releases.md)
