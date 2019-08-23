---
title: <soapProcessing>
ms.date: 03/30/2017
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
ms.openlocfilehash: 678b1f71ac15d3ad30df28cec5abbe403fb08c95
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937058"
---
# <a name="soapprocessing"></a>\<soapProcessing >

Farklı bağlama türleri ve ileti sürümleri arasındaki iletileri sıralamak için kullanılan istemci uç noktası davranışını tanımlar.

**\<sistemin. ServiceModel >**    
&nbsp;&nbsp; **\<davranışlar >**    
&nbsp;&nbsp;&nbsp;&nbsp; **\<Endpointdavranışlar >**    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<davranış >**    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<soapProcessing >**
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<soapProcessing processMessages="true|false" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler  
  
Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|                   | Açıklama |
| ----------------- | ----------- |
| `processMessages` | SOAP iletisi sürümleri arasında iletilerin sıralanması gerekip gerekmediğini belirten bir Boole değeri. |

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|     | Açıklama |
| --- | ----------- |
| [ **\<davranış >** ](behavior-of-endpointbehaviors.md) | Bir uç nokta davranışı belirtir. |

## <a name="remarks"></a>Açıklamalar

SOAP işleme, iletilerin ileti sürümleri arasında dönüştürüldüğü işlemdir.

Windows Communication Foundation (WCF) yönlendirme hizmeti, iletileri bir protokolden diğerine dönüştürebilir. Gelen ve giden Ileti sürümleri farklıysa, doğru sürüme yönelik yeni bir ileti oluşturulur. İletileri <xref:System.ServiceModel.Channels.MessageVersion> bir diğerine işlemek, gelen WCF iletisinden gövde parçasını ve ilgili üstbilgileri içeren yeni bir WCF iletisi oluşturarak gerçekleştirilir. Adresleme 'ye özgü olan veya yönlendirici düzeyinde anlaşılabilecek üstbilgiler, bu üst bilgiler farklı bir sürümdür (örneğin, adresleme üst bilgilerinde) veya bir parçası olarak işlenirken yeni WCF iletisi oluşturma sırasında kullanılmaz. istemci ile yönlendirici arasındaki iletişim.

Giden iletiye bir üstbilginin yerleştirilip yerleştirilmediği, gelen kanal katmanından geçerken anlaşıldığı şekilde işaretlenip işaretlenmediğini belirler. Anlaşılmayan (özel üstbilgiler gibi) üstbilgiler kaldırılmaz ve bu nedenle Giden iletiye kopyalanarak yönlendirme hizmetini geçirin. İletinin gövdesi Giden iletiye kopyalanır. İleti daha sonra giden kanal gönderilir ve bu iletişim protokolüne/taşımasına özgü tüm üst bilgiler ve diğer zarf verileri oluşturulur ve eklenir.

Bu tür işleme adımları SOAP işleme davranışı belirtildiğinde gerçekleşir. [ Bu\<soapprocessingextension >](soapprocessing.md) davranışı, yönlendirme hizmeti başlatıldığında tüm istemci (giden) uç noktalarına uygulanan bir uç nokta davranışıdır. Varsayılan olarak, [ \<yönlendirme >](routing-of-servicebehavior.md) davranışı, her istemci uç noktası için `true` olarak `processMessages` ayarlanmış yeni [ \<bir soapprocessingextension >](soapprocessing.md) davranışı oluşturur ve iliştirir. Yönlendirme hizmetinin anlayamadığı bir protokolüne sahipseniz veya varsayılan işleme davranışını geçersiz kılmak istiyorsanız, tüm yönlendirme hizmeti veya yalnızca belirli uç noktalar için SOAP işlemeyi devre dışı bırakabilirsiniz.  Tüm uç noktalarında yönlendirme hizmeti 'nin tamamına yönelik SOAP işlemeyi devre dışı bırakmak için, `soapProcessing` [ \<yönlendirme >](routing-of-servicebehavior.md) davranışının özniteliğini olarak `false`ayarlayın. Belirli bir uç nokta için SOAP işlemeyi devre dışı bırakmak için, bu davranışı kullanın ve `processMessages` özniteliğini olarak `false`ayarlayın, ardından bu davranışı varsayılan işleme kodunun çalıştırılmasını istemediğiniz uç noktaya ekleyin.  Yönlendirme > davranışı yönlendirme hizmetini ayarlarsa, zaten mevcut olduğundan, uç nokta davranışının yeniden uygulanması atlanacaktır. [ \<](routing-of-servicebehavior.md)
