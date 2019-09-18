---
title: Ek sınıf kitaplıkları ve API'ler
ms.date: 01/29/2018
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: 0aed6f32bbd3ffdc9446e9d17be2d90c62444ee1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053252"
---
# <a name="additional-class-libraries-and-apis"></a>Ek sınıf kitaplıkları ve API'ler

.NET Framework sürekli olarak gelişiyor. Platformlar arası geliştirmeyi artırmak ve yeni işlevselliği erken sunmak için yeni özellikler bant dışı (OOB) olarak serbest bırakılır. Bu konu, için belge sağlamamız gereken OOB projelerini listeler.  
  
Ayrıca, bazı kitaplıklar belirli platformları veya .NET Framework uygulamalarını hedeflemelidir. Örneğin, <xref:System.Text.CodePagesEncodingProvider> sınıfı kod sayfası kodlamalarını .NET Framework kullanılarak geliştirilen UWP uygulamaları için kullanılabilir hale getirir. Bu konu başlığı altında da bu kitaplıklar listelenmektedir.  
  
## <a name="oob-projects"></a>OOB projeleri
  
| Project | Açıklama |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | , İş parçacığı açısından güvenli olan ve içeriklerinin hiçbir şekilde değişmeme garantisi sağlayan koleksiyonlar sağlar. |
| <xref:System.Net.Http.WinHttpHandler> | Windows 'un WinHTTP arabirimine <xref:System.Net.Http.HttpClient> dayalı olarak bir ileti işleyicisi sağlar. |
| <xref:System.Numerics> | SıMD donanım tabanlı hızlandırmasının avantajlarından yararlanan bir vektör türleri kitaplığı sağlar.| 
| <xref:System.Threading.Tasks.Dataflow> | TPL veri akışı kitaplığı, eşzamanlılık özellikli uygulamaların sağlamlığını artırmaya yardımcı olmak için veri akışı bileşenleri sağlar. |  

## <a name="platform-specific-libraries"></a>Platforma özgü kitaplıklar
  
| Project | Açıklama |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Kod sayfası kodlamalarını Evrensel Windows platformu hedefleyen uygulamalar için kullanılabilir hale getirmek için sınıfınıgenişletir.<xref:System.Text.EncodingProvider> |  
  
## <a name="private-apis"></a>Özel API 'Ler  

Bu API 'Ler ürün altyapısını destekler ve doğrudan kodunuzdan kullanılmak üzere tasarlanmamıştır/desteklenmez.  
  
| API adı |
| -------- |
| [System .net. Connection sınıfı](connection.md) |
| [System .net. Connection. d\_writelist alanı](m_writelist.md) |
| [System .net. ConnectionGroup sınıfı](connectiongroup.md) |
| [System.Net.ConnectionGroup.m\_ConnectionList Field](m_connectionlist.md) |
| [System .net. CoreResponseData sınıfı](coreresponsedata.md) |
| [System .net. CoreResponseData. d\_ResponseHeaders alanı](coreresponsedata_m_responseheaders.md) |
| [System .net. CoreResponseData.\_mstatuscode alanı](coreresponsedata_m_statuscode.md) |
| [Sistem .net. HttpWebRequest. \_Oto yeniden yönlendirmeler alanı](_autoredirects.md) |
| [Sistem .net. HttpWebRequest. \_CoreResponse alanı](httpwebrequest__coreresponse.md) |
| [Sistem .net. HttpWebRequest. \_HttpResponse alanı](_httpresponse.md) |
| [System.Net.ServicePoint.m\_ConnectionGroupList Field](m_connectiongrouplist.md) |
| [System.Net.ServicePointManager.s\_ServicePointTable Field](s_servicepointtable.md) |
| [System. Windows. Diagnostics. VisualDiagnostics. s\_ıdebuggercheckdisabledfortestamaçlar alanı](s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [System. Windows. Forms. Design. DataMemberFieldEditor sınıfı](datamemberfieldeditor-class.md) |
| [System. Windows. Forms. Design. Datamemberlistedıtor sınıfı](datamemberlisteditor-class.md) |
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework ve Bant Dışı Yayınlar](../get-started/the-net-framework-and-out-of-band-releases.md)
