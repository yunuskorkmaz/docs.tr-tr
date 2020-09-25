---
title: WCF Veri Hizmetleri Protokol Uygulama Ayrıntıları
ms.date: 03/30/2017
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
ms.openlocfilehash: 0723d5a473bb87b8bd464a944a5c68f1a8d3f5da
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202168"
---
# <a name="wcf-data-services-protocol-implementation-details"></a>WCF Veri Hizmetleri Protokol Uygulama Ayrıntıları

## <a name="odata-protocol-implementation-details"></a>OData protokol uygulama ayrıntıları  

Açık Veri Protokolü (OData), protokolü uygulayan bir veri hizmetinin belirli bir minimum işlevler kümesini sağlamasını gerektirir. Bu işlevler, "gereken" ve "gereken" koşullarda protokol belgelerinde açıklanmıştır. Diğer isteğe bağlı işlevler "Mayıs" terimlerinde açıklanmıştır. Bu makalede, şu anda WCF Veri Hizmetleri tarafından uygulanmayan bu isteğe bağlı işlevler açıklanır.
  
### <a name="support-for-the-format-query-option"></a>$format sorgu seçeneği için destek  

 OData protokolü hem JavaScript gösterimini (JSON) hem de Atom akışlarını destekler ve OData, `$format` bir istemcinin yanıt akışı biçimini istemesine izin vermek için sistem sorgu seçeneğini sağlar. Veri hizmeti tarafından destekleniyorsa, bu sistem sorgu seçeneği isteğin Accept üst bilgisinin değerini geçersiz kılmalıdır. WCF Veri Hizmetleri hem JSON hem de Atom akışlarını döndürmeyi destekler. Ancak, varsayılan uygulama `$format` sorgu seçeneğini desteklemez ve yanıtın biçimini belirlemekte yalnızca Accept üst bilgisinin değerini kullanır. Veri hizmetinizin `$format` , kabul üst bilgisini ayarlayaamadığı durumlar gibi sorgu seçeneğini desteklemesi gerekebilecek durumlar vardır. Bu senaryoları desteklemek için veri hizmetinizi URI 'deki bu seçeneği işleyecek şekilde genişletmelidir. [ADO.NET Data Services örnek projesi Için JSONP ve URL denetimli biçim DESTEĞINI](https://go.microsoft.com/fwlink/?LinkId=208228) MSDN Kod Galerisi Web sitesinden indirerek ve veri hizmeti projenize ekleyerek bu işlevselliği veri hizmetinize ekleyebilirsiniz. Bu örnek, `$format` sorgu seçeneğini kaldırır ve Accept üst bilgisini olarak değiştirir `application/json` . Örnek projeyi dahil ettiğinizde ve `JSONPSupportBehaviorAttribute` veri hizmeti sınıfına eklemek, hizmetin `$format` sorgu seçeneğini işlemesini sağlar `$format=json` . Bu örnek projenin daha fazla özelleştirilmesi için de `$format=atom` veya diğer özel biçimlerin işlenmesi gerekir.  
  
## <a name="wcf-data-services-behaviors"></a>WCF Veri Hizmetleri davranışları  

 Aşağıdaki WCF Veri Hizmetleri davranışları OData protokolü tarafından açıkça tanımlanmamıştır:  
  
### <a name="default-sorting-behavior"></a>Varsayılan sıralama davranışı  

 Veri hizmetine gönderilen bir sorgu isteği bir `$top` veya `$skip` sistem sorgu seçeneği içerdiğinde ve `$orderby` sistem sorgu seçeneğini içermiyorsa, döndürülen akış, anahtar özelliklerine göre artan sırada sıralanır. Bunun nedeni, sonuçların doğru sayfalamamasından emin olmak için sıralama gerektirdir. Bunu yapmak için, veri hizmeti sorguya bir sıralama ifadesi ekler. Bu davranış, veri hizmetinde sunucu odaklı sayfalama etkinleştirildiğinde da oluşur. Daha fazla bilgi için bkz. [veri hizmetini yapılandırma](configuring-the-data-service-wcf-data-services.md). Döndürülen akışın sıralamasını denetlemek için `$orderby` sorgu URI 'sine dahil etmelisiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)
- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
