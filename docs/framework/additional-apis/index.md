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
# <a name="additional-class-libraries-and-apis"></a>Ek sınıf kitaplıkları ve API'ler

.NET Framework sürekli gelişmektedir. Platformlar arası geliştirmeyi geliştirmek ve yeni işlevleri erken tanıtmak için, yeni özellikler banttan (OOB) çıkar. Bu konu, dokümantasyon sağladığımız OOB projelerini listeler.  
  
Ayrıca, bazı kitaplıklar .NET Framework'ün belirli platformlarını veya uygulamalarını hedef alır. Örneğin, <xref:System.Text.CodePagesEncodingProvider> sınıf kod sayfası kodlamalarını .NET Framework kullanılarak geliştirilen UWP uygulamalarında kullanılabilir hale getirir. Bu konu, bu kitaplıkları da listeler.  
  
## <a name="oob-projects"></a>OOB projeleri
  
| Project | Açıklama |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | İş parçacığı güvenli ve içeriğini asla değiştirmez garanti koleksiyonları sağlar. |
| <xref:System.Net.Http.WinHttpHandler> | Windows'un WinHTTP <xref:System.Net.Http.HttpClient> arabirimini temel alan bir ileti işleyicisi sağlar. |
| <xref:System.Numerics> | SIMD donanım tabanlı ivmeden yararlanabilecek vektör türlerinin kitaplıklarını sağlar.|
| <xref:System.Threading.Tasks.Dataflow> | TPL Dataflow Kitaplığı, eşzamanlılık özellikli uygulamaların sağlamlığını artırmaya yardımcı olmak için veri akışı bileşenleri sağlar. |  

## <a name="platform-specific-libraries"></a>Platforma özel kütüphaneler
  
| Project | Açıklama |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Evrensel Windows <xref:System.Text.EncodingProvider> Platformu'nu hedefleyen uygulamalar için kod sayfası kodlamalarını kullanılabilir hale getirmek için sınıfı genişletir. |  
  
## <a name="private-apis"></a>Özel API'ler  

Bu API'ler ürün altyapısını destekler ve doğrudan kodunuzdakullanılmak üzere tasarlanmamıştır/desteklenmez.  
  
* [Microsoft.SqlServer.Server.SmiOrderProperty.Item Özellik](microsoft.sqlserver.server.smiorderproperty.item.md)
* [System.Exception.PrepForRemoting Yöntemi](system.exception.prepforremoting.md)
* [System.Data.SqlTypes.SqlChars.Stream Özelliği](system.data.sqltypes.sqlchars.stream.md)
* [System.Data.SqlTypes.SqlStreamChars Constructor](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [System.Data.SqlTypes.SqlStreamChars.CanSeek Özelliği](system.data.sqltypes.sqlstreamchars.canseek.md)
* [System.Data.SqlTypes.SqlStreamChars.IsNull Özelliği](system.data.sqltypes.sqlstreamchars.isnull.md)
* [System.Data.SqlTypes.SqlStreamChars.Length Özelliği](system.data.sqltypes.sqlstreamchars.length.md)
* [System.Data.SqlTypes.SqlStreamChars.Close Metodu](system.data.sqltypes.sqlstreamchars.close.md)
* [System.Data.SqlTypes.SqlStreamChars.Dispose Yöntemi](system.data.sqltypes.sqlstreamchars.dispose.md)
* [System.Data.SqlTypes.SqlStreamChars.Flush Yöntemi](system.data.sqltypes.sqlstreamchars.flush.md)
* [System.Data.SqlTypes.SqlStreamChars.Read Metodu](system.data.sqltypes.sqlstreamchars.read.md)
* [System.Data.SqlTypes.SqlStreamChars.Seek Yöntemi](system.data.sqltypes.sqlstreamchars.seek.md)
* [System.Data.SqlTypes.SqlStreamChars.SetLength Yöntemi](system.data.sqltypes.sqlstreamchars.setlength.md)
* [System.Data.SqlTypes.SqlStreamChars.Write Metodu](system.data.sqltypes.sqlstreamchars.write.md)
* [System.io.MemoryStream.internalgetoriginandlength yöntemi](system.io.memorystream.internalgetoriginandlength.md)
* [System.Net.Connection Sınıfı](connection.md)
* [System.Net.Connection.m\_YazmaListesi Alanı](m_writelist.md)
* [System.Net.ConnectionGroup Sınıfı](connectiongroup.md)
* [System.Net.ConnectionGroup.m\_ConnectionList Alanı](m_connectionlist.md)
* [System.Net.ConnectStream.Connection Özelliği](system.net.connectstream.connection.md)
* [System.Net.CoreResponseData Sınıfı](coreresponsedata.md)
* [System.Net.CoreResponseData.m\_ResponseHeaders Alanı](coreresponsedata_m_responseheaders.md)
* [System.Net.CoreResponseData.m\_StatusCode Alanı](coreresponsedata_m_statuscode.md)
* [System.Net.httpWebRequest. \_AutoRedirects Alanı](_autoredirects.md)
* [System.Net.httpWebRequest. \_CoreResponse Alanı](httpwebrequest__coreresponse.md)
* [System.Net.httpWebRequest. \_httpResponse Alanı](_httpresponse.md)
* [System.Net.PooledStream.NetworkStream Özelliği](system.net.pooledstream.networkstream.md)
* [System.Net.RtcState sınıfı](system.net.rtcstate.md)
* [System.Net.ServicePoint.m\_ConnectionGroupList Alanı](m_connectiongrouplist.md)
* [System.Net.ServicePointManager.s\_ServicePointTable Alanı](s_servicepointtable.md)
* [System.Net.TlsStream.m_Worker Alanı](system.net.tlsstream.m_worker.md)
* [System.Net.Security.SslState.SslProtocol Özelliği](system.net.security.sslstate.sslprotocol.md)
* [System.ServiceModel.Channels.Message.BodyToString Yöntemi](system.servicemodel.channels.message.bodytostring.md)
* [System.ServiceModel.Channels.Message.WriteStartHeaders Yöntemi](system.servicemodel.channels.message.writestartheaders.md)
* [System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Alan](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [System.Windows.Forms.Design.DataMemberFieldEditor Sınıfı](datamemberfieldeditor-class.md)
* [System.Windows.Forms.Design.DataMemberListEditor Sınıfı](datamemberlisteditor-class.md)
* [System.Xml.XmlReader.CreateSqlReader Yöntemi](system.xml.xmlreader.createsqlreader.md)
* [Adodb. Bağlantı Arabirimi](adodb.connection.md)
* [Adodb. OlayReason Enum](adodb.eventreasonenum.md)
* [Adodb. OlayDurum Enum](adodb.eventstatusenum.md)
* [stdole. DISPPARAMS Yapısı](stdole.dispparams.md)
* [stdole. EXCEPINFO Yapısı](stdole.excepinfo.md)
* [stdole. IFont.Name Özelliği](stdole.ifont.name.md)
* [stdole. IFontDisp Arayüzü](stdole.ifontdisp.md)
* [stdole. IPicture.Handle Özelliği](stdole.ipicture.handle.md)
* [stdole. IPictureDisp.Handle Özelliği](stdole.ipicturedisp.handle.md)
* [stdole. StdFont Arayüzü](stdole.stdfont.md)
* [stdole. StdPicture Arayüzü](stdole.stdpicture.md)
  
## <a name="see-also"></a>Ayrıca bkz.

* [.NET Framework ve Bant Dışı Yayınlar](../get-started/the-net-framework-and-out-of-band-releases.md)
