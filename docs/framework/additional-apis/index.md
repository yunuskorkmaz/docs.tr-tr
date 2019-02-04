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
ms.openlocfilehash: a48a145cd337a18c4ce63b281e1c82032d0532e7
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674418"
---
# <a name="additional-class-libraries-and-apis"></a>Ek sınıf kitaplıkları ve API'ler

.NET Framework sürekli gelişmektedir. Platformlar arası geliştirmeyi geliştirmek ve erken yeni işlevleri tanıtmak için yeni özellikleri bant dışında (OOB) yayınlanır. Bu konuda size sağladığımız belgeleri için OOB projeleri listeler.  
  
Ayrıca, bazı kitaplıklar belirli platformlara veya .NET Framework uygulamaları hedefler. Örneğin, <xref:System.Text.CodePagesEncodingProvider> sınıfı kod sayfası kodlamaları için UWP uygulamaları .NET Framework kullanılarak geliştirilmiş kullanıma sunar. Bu konuda, bu kitaplıkların da listelenir.  
  
## <a name="oob-projects"></a>OOB projeleri
  
| Proje | Açıklama |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | İş parçacığı güvenli ve hiçbir zaman içeriklerini değiştirmek için kesin koleksiyonlar sağlar. |
| <xref:System.Net.Http.WinHttpHandler> | Bir ileti işleyicisi sağlar <xref:System.Net.Http.HttpClient> Windows WinHTTP arabirimi esas alan. |
| <xref:System.Numerics> | SIMD donanım tabanlı hızlandırma yararlanabilirsiniz vektör türleri içeren bir kitaplık sağlar.| 
| <xref:System.Threading.Tasks.Dataflow> | TPL veri akışı kitaplığı, eşzamanlılık kullanan uygulamaların sağlamlığını artırmak için veri akışı bileşenleri sağlar. |  

## <a name="platform-specific-libraries"></a>Platforma özgü kitaplıklar
  
| Proje | Açıklama |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Genişletir <xref:System.Text.EncodingProvider> kod sayfası kodlamaları hedefleyen Evrensel Windows platformu uygulamaları için kullanılabilir hale getirmek için sınıf. |  
  
## <a name="private-apis"></a>Özel API'ler  

Bu API, ürün altyapısını destekler ve amaçlayan/desteklenen doğrudan sizin kodunuzdan kullanılmak üzere değildir.  
  
| API adı |
| -------- |
| [System.Net.Connection sınıfı](../../../docs/framework/additional-apis/connection.md) |
| [System.Net.Connection.m\_WriteList alan](../../../docs/framework/additional-apis/m_writelist.md) |
| [System.Net.ConnectionGroup Class](../../../docs/framework/additional-apis/connectiongroup.md) |
| [System.Net.ConnectionGroup.m\_ConnectionList Field](../../../docs/framework/additional-apis/m_connectionlist.md) |
| [System.Net.CoreResponseData Class](../../../docs/framework/additional-apis/coreresponsedata.md) |
| [System.Net.CoreResponseData.m\_ResponseHeaders Field](../../../docs/framework/additional-apis/coreresponsedata_m_responseheaders.md) |
| [System.Net.CoreResponseData.m\_StatusCode Field](../../../docs/framework/additional-apis/coreresponsedata_m_statuscode.md) |
| [System.Net.HttpWebRequest. \_AutoRedirects alan](../../../docs/framework/additional-apis/_autoredirects.md) |
| [System.Net.HttpWebRequest. \_CoreResponse alan](../../../docs/framework/additional-apis/httpwebrequest__coreresponse.md) |
| [System.Net.HttpWebRequest. \_HttpResponse alan](../../../docs/framework/additional-apis/_httpresponse.md) |
| [System.Net.ServicePoint.m\_ConnectionGroupList Field](../../../docs/framework/additional-apis/m_connectiongrouplist.md) |
| [System.Net.ServicePointManager.s\_ServicePointTable Field](../../../docs/framework/additional-apis/s_servicepointtable.md) |
| [System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes alan](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [System.Windows.Forms.Design.DataMemberFieldEditor sınıfı](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |
| [System.Windows.Forms.Design.DataMemberListEditor sınıfı](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework ve Bant Dışı Yayınlar](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)
