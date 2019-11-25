---
title: WCF Veri Hizmetleri Protokol Uygulama Ayrıntıları
ms.date: 03/30/2017
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
ms.openlocfilehash: 10a330fd6f6f73ffc7e812e0a9012ec20c83861d
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975043"
---
# <a name="wcf-data-services-protocol-implementation-details"></a>WCF Veri Hizmetleri Protokol Uygulama Ayrıntıları
## <a name="odata-protocol-implementation-details"></a>OData protokol uygulama ayrıntıları  
 Açık Veri Protokolü (OData), protokolü uygulayan bir veri hizmetinin belirli bir minimum işlevler kümesini sağlamasını gerektirir. Bu işlevler, protokol belgelerinde "şunları yapmalısınız" ve "gerekir." olarak açıklanmaktadır. Diğer isteğe bağlı işlevler "Mayıs" terimlerinde açıklanmıştır. Bu konu, şu anda [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]tarafından uygulanmayan bu isteğe bağlı işlevleri açıklamaktadır. Daha fazla bilgi için bkz. [OData protokolü belgeleri](https://go.microsoft.com/fwlink/?LinkID=184554).  
  
### <a name="support-for-the-format-query-option"></a>$format sorgu seçeneği için destek  
 OData protokolü hem JavaScript gösterimini (JSON) hem de Atom akışlarını destekler ve OData, bir istemcinin yanıt akışı biçimini istemesine izin vermek için `$format` sistem sorgu seçeneğini sağlar. Veri hizmeti tarafından destekleniyorsa, bu sistem sorgu seçeneği isteğin Accept üst bilgisinin değerini geçersiz kılmalıdır. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] hem JSON hem de Atom akışlarını döndürmeyi destekler. Ancak, varsayılan uygulama `$format` sorgu seçeneğini desteklemez ve yanıt biçimini belirlemekte yalnızca Accept üst bilgisinin değerini kullanır. Veri hizmetinizin, kabul üst bilgisini ayarlayaamadığı durumlar gibi `$format` sorgu seçeneğini desteklemesi gerekebilecek durumlar vardır. Bu senaryoları desteklemek için veri hizmetinizi URI 'deki bu seçeneği işleyecek şekilde genişletmelidir. [ADO.NET Data Services örnek projesi Için JSONP ve URL denetimli biçim DESTEĞINI](https://go.microsoft.com/fwlink/?LinkId=208228) MSDN Kod Galerisi Web sitesinden indirerek ve veri hizmeti projenize ekleyerek bu işlevselliği veri hizmetinize ekleyebilirsiniz. Bu örnek `$format` sorgu seçeneğini kaldırır ve Accept üst bilgisini `application/json`olarak değiştirir. Örnek projeyi dahil ettiğinizde ve veri hizmeti sınıfınız `JSONPSupportBehaviorAttribute` eklendiğinde, hizmetin `$format` sorgu seçeneği `$format=json`işlemesini sağlar. Bu örnek projenin daha fazla özelleştirilmesi, `$format=atom` veya diğer özel biçimleri işlemek için de gereklidir.  
  
## <a name="wcf-data-services-behaviors"></a>WCF Veri Hizmetleri davranışları  
 Aşağıdaki [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] davranışları OData protokolü tarafından açıkça tanımlanmamıştır:  
  
### <a name="default-sorting-behavior"></a>Varsayılan sıralama davranışı  
 Veri hizmetine gönderilen bir sorgu isteği bir `$top` veya `$skip` sistem sorgusu seçeneği içerdiğinde ve `$orderby` sistem sorgu seçeneğini içermiyorsa, döndürülen akış anahtar özelliklerine göre artan sırada sıralanır. Bunun nedeni, sonuçların doğru sayfalamamasından emin olmak için sıralama gerektirdir. Bunu yapmak için, veri hizmeti sorguya bir sıralama ifadesi ekler. Bu davranış, veri hizmetinde sunucu odaklı sayfalama etkinleştirildiğinde da oluşur. Daha fazla bilgi için bkz. [veri hizmetini yapılandırma](configuring-the-data-service-wcf-data-services.md). Döndürülen akışın sıralamasını denetlemek için sorgu URI 'sine `$orderby` dahil etmelisiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)
- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
