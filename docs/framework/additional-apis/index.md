---
title: Ek sınıf kitaplıkları ve API'ler
ms.date: 10/17/2019
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: 809ac026244b24aee69ec0d6c40c10a1248c234c
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579112"
---
# <a name="additional-class-libraries-and-apis"></a>Ek sınıf kitaplıkları ve API'ler

.NET Framework sürekli olarak gelişiyor. Platformlar arası geliştirmeyi artırmak ve yeni işlevselliği erken sunmak için yeni özellikler bant dışı (OOB) olarak serbest bırakılır. Bu konu, için belge sağlamamız gereken OOB projelerini listeler.  
  
Ayrıca, bazı kitaplıklar belirli platformları veya .NET Framework uygulamalarını hedeflemelidir. Örneğin <xref:System.Text.CodePagesEncodingProvider> sınıfı, kod sayfası kodlamaları .NET Framework kullanılarak geliştirilen UWP uygulamaları için kullanılabilir hale getirir. Bu konu başlığı altında da bu kitaplıklar listelenmektedir.  
  
## <a name="oob-projects"></a>OOB projeleri
  
| Project | Açıklama |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | , İş parçacığı açısından güvenli olan ve içeriklerinin hiçbir şekilde değişmeme garantisi sağlayan koleksiyonlar sağlar. |
| <xref:System.Net.Http.WinHttpHandler> | Windows 'un WinHTTP arabirimine göre <xref:System.Net.Http.HttpClient> için bir ileti işleyicisi sağlar. |
| <xref:System.Numerics> | SıMD donanım tabanlı hızlandırmasının avantajlarından yararlanan bir vektör türleri kitaplığı sağlar.| 
| <xref:System.Threading.Tasks.Dataflow> | TPL veri akışı kitaplığı, eşzamanlılık özellikli uygulamaların sağlamlığını artırmaya yardımcı olmak için veri akışı bileşenleri sağlar. |  

## <a name="platform-specific-libraries"></a>Platforma özgü kitaplıklar
  
| Project | Açıklama |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Kod sayfası kodlamalarını Evrensel Windows Platformu hedefleyen uygulamalar için kullanılabilir hale getirmek için <xref:System.Text.EncodingProvider> sınıfını genişletir. |  
  
## <a name="private-apis"></a>Özel API 'Ler  

Bu API 'Ler ürün altyapısını destekler ve doğrudan kodunuzdan kullanılmak üzere tasarlanmamıştır/desteklenmez.  
  
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
* [System .net. Connection sınıfı](connection.md)
* [System .net. Connection. d \_WriteList alanı](m_writelist.md)
* [System .net. ConnectionGroup sınıfı](connectiongroup.md)
* [System .net. ConnectionGroup. d \_ConnectionList alanı](m_connectionlist.md)
* [System .net. CoreResponseData sınıfı](coreresponsedata.md)
* [System .net. CoreResponseData. d \_ResponseHeaders alanı](coreresponsedata_m_responseheaders.md)
* [System .net. CoreResponseData. d \_StatusCode alanı](coreresponsedata_m_statuscode.md)
* [System .net. HttpWebRequest. \_AutoRedirects alanı](_autoredirects.md)
* [System .net. HttpWebRequest. \_CoreResponse alanı](httpwebrequest__coreresponse.md)
* [System .net. HttpWebRequest. \_HttpResponse alanı](_httpresponse.md)
* [System .net. ServicePoint. d \_ConnectionGroupList alanı](m_connectiongrouplist.md)
* [System .net. ServicePointManager. s \_ServicePointTable alanı](s_servicepointtable.md)
* [System. Windows. Diagnostics. VisualDiagnostics. s \_isDebuggerCheckDisabledForTestPurposes alanı](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [System. Windows. Forms. Design. DataMemberFieldEditor sınıfı](datamemberfieldeditor-class.md)
* [System. Windows. Forms. Design. Datamemberlistedıtor sınıfı](datamemberlisteditor-class.md)
* [System. xml. XmlReader. CreateSqlReader yöntemi](system.xml.xmlreader.createsqlreader.md)
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

* [.NET Framework ve Bant Dışı Yayınlar](../get-started/the-net-framework-and-out-of-band-releases.md)
