---
title: Ek sınıf kitaplıkları ve API'leri
ms.custom: ''
ms.date: 01/29/2018
ms.prod: .net-framework-oob
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
caps.latest.revision: 12
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d9ceb1ad24d4ba87fab7713ba61fed91eef26c4d
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="additional-class-libraries-and-apis"></a>Ek sınıf kitaplıkları ve API'leri

.NET Framework sürekli gelişen ve platformlar arası geliştirme geliştirmek için veya yeni işlevsellik erken müşterilerimizin tanıtmak için şu yeni özellikler bant dışı (OOB) dışında bırakın. Bu konuda belgelerine sağladığımız OOB projeleri listeler.  
  
Ayrıca, bazı kitaplıklar belirli platformlar veya .NET Framework uygulamaları hedefleyin. Örneğin, <xref:System.Text.CodePagesEncodingProvider> sınıfı kod sayfası Kodlamalar .NET Framework kullanılarak geliştirilmiş UWP uygulamaları için kullanılabilir yapar. Bu konuda Bu kitaplıklar de listelenir.  
  
## <a name="oob-projects"></a>OOB projeleri
  
| Proje | Açıklama |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | İş parçacığı güvenli ve hiçbir zaman içeriklerini değiştirmek için garantili olan koleksiyonları sağlar. |
| <xref:System.Net.Http.WinHttpHandler> | Bir ileti işleyicisi sağlar <xref:System.Net.Http.HttpClient> Windows WinHTTP arabirimi esas alan. |
| [System.Numerics.Vectors](https://msdn.microsoft.com/library/mt452176.aspx) | Bir kitaplık SIMD donanım tabanlı hızlandırma yararlanabilir vektör türleri sağlar.| 
| <xref:System.Threading.Tasks.Dataflow> | TPL veri akışı kitaplığı eşzamanlılık özellikli uygulamalar'ların sağlamlığını artırmak için veri akışı bileşenleri sağlar. |  

## <a name="platform-specific-libraries"></a>Platforma özgü kitaplıkları
  
| Proje | Açıklama |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Genişletir <xref:System.Text.EncodingProvider> kod sayfası Kodlamalar Evrensel Windows platformu hedefleyen uygulamalar kullanılabilir hale getirmek için sınıf. |  
  
## <a name="private-apis"></a>Özel API'leri  

Bu API ürün altyapısını destekleyen ve amaçlanan/desteklenen doğrudan kodunuzdan kullanılmak üzere değildir.  
  
| API adı |
| -------- |
| [System.Net.Connection Class](../../../docs/framework/additional-apis/connection.md) |
| [System.Net.Connection.m\_WriteList alan](../../../docs/framework/additional-apis/m_writelist.md) |
| [System.Net.ConnectionGroup Class](../../../docs/framework/additional-apis/connectiongroup.md) |
| [System.Net.ConnectionGroup.m\_ConnectionList Field](../../../docs/framework/additional-apis/m_connectionlist.md) |
| [System.Net.CoreResponseData Class](../../../docs/framework/additional-apis/coreresponsedata.md) |
| [System.Net.CoreResponseData.m\_ResponseHeaders Field](../../../docs/framework/additional-apis/coreresponsedata_m_responseheaders.md) |
| [System.Net.CoreResponseData.m\_StatusCode Field](../../../docs/framework/additional-apis/coreresponsedata_m_statuscode.md) |
| [System.Net.HttpWebRequest.\_AutoRedirects Field](../../../docs/framework/additional-apis/_autoredirects.md) |
| [System.Net.HttpWebRequest.\_CoreResponse Field](../../../docs/framework/additional-apis/httpwebrequest__coreresponse.md) |
| [System.Net.HttpWebRequest. \_HttpResponse alan](../../../docs/framework/additional-apis/_httpresponse.md) |
| [System.Net.ServicePoint.m\_ConnectionGroupList Field](../../../docs/framework/additional-apis/m_connectiongrouplist.md) |
| [System.Net.ServicePointManager.s\_ServicePointTable Field](../../../docs/framework/additional-apis/s_servicepointtable.md) |
| [System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes alan](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [System.Windows.Forms.Design.DataMemberFieldEditor Class](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |
| [System.Windows.Forms.Design.DataMemberListEditor Class](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |
  
## <a name="see-also"></a>Ayrıca bkz.

[.NET Framework ve Bant Dışı Yayınlar](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)
