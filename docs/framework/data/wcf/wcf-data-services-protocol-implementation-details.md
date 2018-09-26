---
title: WCF Veri Hizmetleri protokol uygulama ayrıntıları
ms.date: 03/30/2017
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
ms.openlocfilehash: 1d68e278fbac0137d1a5b2dca2daedba2294a7ee
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47195686"
---
# <a name="wcf-data-services-protocol-implementation-details"></a>WCF Veri Hizmetleri protokol uygulama ayrıntıları
## <a name="odata-protocol-implementation-details"></a>OData protokol uygulama ayrıntıları  
 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Protokolü uygulayan bir veri hizmeti işlevleri belirli minimum düzeyde sağlamanızı gerektirir. Bu işlevler "gerekir" ve "gerekir." açısından Protokolü belgelerinde açıklanmıştır İsteğe bağlı diğer işlevleri "Mayıs" açısından açıklanır Bu konuda, şu anda tarafından uygulanmadı Bu isteğe bağlı işlevler açıklanmaktadır. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Daha fazla bilgi için [OData Protokolü belgeleri](https://go.microsoft.com/fwlink/?LinkID=184554).  
  
### <a name="support-for-the-format-query-option"></a>$Format sorgu seçeneği için destek  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Protokolünü destekleyen JavaScript gösterimi (JSON) hem Atom akışları ve [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] sağlar `$format` akışı yanıtın biçimini istemek bir istemci izin verecek şekilde sistem sorgusu seçeneği. Bu sistem sorgusu seçeneği veri hizmeti tarafından destekleniyorsa, isteğin bir Accept üst bilgisi değeri geçersiz kılmanız gerekir. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] hem JSON hem de Atom akışları döndüren destekler. Bununla birlikte, varsayılan uygulama desteklemediği `$format` sorgu seçeneği ve yanıtın biçimini belirlemek için yalnızca bir Accept üst bilgisi değeri kullanır. Bazı durumlarda veri hizmetinizi desteklemesi gerekebilir `$format` sorgu seçeneği gibi olduğunda istemciler Accept üst bilgisi olarak ayarlanamıyor. Bu senaryoları desteklemek için bu seçeneği urı'sindeki işlemek için veri hizmetinizi genişletmeniz gerekir. Yükleyerek bu işlevler, veri hizmetine ekleyebilirsiniz [JSONP ve URL denetimli biçimi desteklemek için ADO.NET Data Services](https://go.microsoft.com/fwlink/?LinkId=208228) kodunuzla MSDN Kod Galerisi web sitesi ve veri hizmeti projenize ekleme. Bu örnek kaldırır `$format` sorgu seçeneği için Accept üst bilgisi değiştirir `application/json`. Dahil ettiğinizde örnek proje ve ekleme `JSONPSupportBehaviorAttribute` verilerinize hizmet sınıfı hizmet sağlayan `$format` sorgu seçeneği `$format=json`. Bu örnek projesinin daha fazla özelleştirme ayrıca işlemek için gerekli `$format=atom` veya diğer özel biçimler.  
  
## <a name="wcf-data-services-behaviors"></a>Davranışlar WCF Veri Hizmetleri  
 Aşağıdaki [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] davranışları açıkça tanımlanmamış tarafından [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokolü:  
  
### <a name="default-sorting-behavior"></a>Varsayılan sıralama davranışı  
 Ne zaman veri hizmetine gönderilen bir sorgu isteği içeren bir `$top` veya `$skip` sistem sorgusu seçeneği ve içermemesi `$orderby` sistem sorgusu seçeneği, döndürülen akışa göre artan düzende anahtar özellikleri sıralandığı. Sıralama doğru disk belleği sonuçları sağlamak için gerekli olmasıdır. Bunu yapmak için veri hizmeti sorgusuna bir sıralama ifadesi ekler. Bu davranış, aynı zamanda sunucu tabanlı disk belleği veri hizmeti etkin olduğunda oluşur. Daha fazla bilgi için [veri hizmeti yapılandırma](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). Sıralama oluşan döndürülen akışını denetlemek için içermelidir `$orderby` URI sorgu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Veri Hizmetlerini Tanımlama](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [WCF Veri Hizmetleri İstemci Kitaplığı](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
