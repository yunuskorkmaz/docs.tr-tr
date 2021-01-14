---
title: WCF Veri Hizmetleri Protokol Uygulama Ayrıntıları
ms.date: 03/30/2017
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
ms.openlocfilehash: a9b996671f2d8b57593f80fb13e966c5f03a2801
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190396"
---
# <a name="wcf-data-services-protocol-implementation-details"></a>WCF Veri Hizmetleri Protokol Uygulama Ayrıntıları

## <a name="odata-protocol-implementation-details"></a>OData protokol uygulama ayrıntıları  

Açık Veri Protokolü (OData), protokolü uygulayan bir veri hizmetinin belirli bir minimum işlevler kümesini sağlamasını gerektirir. Bu işlevler, "gereken" ve "gereken" koşullarda protokol belgelerinde açıklanmıştır. Diğer isteğe bağlı işlevler "Mayıs" terimlerinde açıklanmıştır. Bu makalede, şu anda WCF Veri Hizmetleri tarafından uygulanmayan bu isteğe bağlı işlevler açıklanır.
  
### <a name="support-for-the-format-query-option"></a>$format sorgu seçeneği için destek  

 OData protokolü hem JavaScript gösterimini (JSON) hem de Atom akışlarını destekler ve OData, `$format` bir istemcinin yanıt akışı biçimini istemesine izin vermek için sistem sorgu seçeneğini sağlar. Veri hizmeti tarafından destekleniyorsa, bu sistem sorgu seçeneği isteğin Accept üst bilgisinin değerini geçersiz kılmalıdır. WCF Veri Hizmetleri hem JSON hem de Atom akışlarını döndürmeyi destekler. Ancak, varsayılan uygulama `$format` sorgu seçeneğini desteklemez ve yanıtın biçimini belirlemekte yalnızca Accept üst bilgisinin değerini kullanır. Veri hizmetinizin `$format` , kabul üst bilgisini ayarlayaamadığı durumlar gibi sorgu seçeneğini desteklemesi gerekebilecek durumlar vardır. Bu senaryoları desteklemek için veri hizmetinizi URI 'deki bu seçeneği işleyecek şekilde genişletmelidir.
  
## <a name="wcf-data-services-behaviors"></a>WCF Veri Hizmetleri davranışları  

 Aşağıdaki WCF Veri Hizmetleri davranışları OData protokolü tarafından açıkça tanımlanmamıştır:  
  
### <a name="default-sorting-behavior"></a>Varsayılan sıralama davranışı  

 Veri hizmetine gönderilen bir sorgu isteği bir `$top` veya `$skip` sistem sorgu seçeneği içerdiğinde ve `$orderby` sistem sorgu seçeneğini içermiyorsa, döndürülen akış, anahtar özelliklerine göre artan sırada sıralanır. Bunun nedeni, sonuçların doğru sayfalamamasından emin olmak için sıralama gerektirdir. Bunu yapmak için, veri hizmeti sorguya bir sıralama ifadesi ekler. Bu davranış, veri hizmetinde sunucu odaklı sayfalama etkinleştirildiğinde da oluşur. Daha fazla bilgi için bkz. [veri hizmetini yapılandırma](configuring-the-data-service-wcf-data-services.md). Döndürülen akışın sıralamasını denetlemek için `$orderby` sorgu URI 'sine dahil etmelisiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Veri Hizmetlerini Tanımlama](defining-wcf-data-services.md)
- [WCF Veri Hizmetleri İstemci Kitaplığı](wcf-data-services-client-library.md)
