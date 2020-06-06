---
title: <soapProcessing>
ms.date: 03/30/2017
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
ms.openlocfilehash: 0728e22205d4ac2c7674f7690e142aed51d42440
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399536"
---
# \<soapProcessing>

Farklı bağlama türleri ve ileti sürümleri arasındaki iletileri sıralamak için kullanılan istemci uç noktası davranışını tanımlar.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing>**
  
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

Yok

### <a name="parent-elements"></a>Üst öğeler

|     | Açıklama |
| --- | ----------- |
| [**\<behavior>**](behavior-of-endpointbehaviors.md) | Bir uç nokta davranışı belirtir. |

## <a name="remarks"></a>Açıklamalar

SOAP işleme, iletilerin ileti sürümleri arasında dönüştürüldüğü işlemdir.

Windows Communication Foundation (WCF) yönlendirme hizmeti, iletileri bir protokolden diğerine dönüştürebilir. Gelen ve giden Ileti sürümleri farklıysa, doğru sürüme yönelik yeni bir ileti oluşturulur. İletileri bir diğerine işlemek <xref:System.ServiceModel.Channels.MessageVersion> , gelen WCF iletisinden gövde parçasını ve ilgili üstbilgileri içeren yeni BIR WCF iletisi oluşturarak gerçekleştirilir. Adresleme 'ye özgü olan veya yönlendirici düzeyinde anlaşılabilecek üstbilgiler, bu üst bilgiler farklı bir sürümlük (adresleme üstbilgileri durumunda) veya istemci ile yönlendirici arasındaki iletişimin bir parçası olarak işlendiği için yeni WCF iletisinin oluşturulması sırasında kullanılmaz.

Giden iletiye bir üstbilginin yerleştirilip yerleştirilmediği, gelen kanal katmanından geçerken anlaşıldığı şekilde işaretlenip işaretlenmediğini belirler. Anlaşılmayan (özel üstbilgiler gibi) üstbilgiler kaldırılmaz ve bu nedenle Giden iletiye kopyalanarak yönlendirme hizmetini geçirin. İletinin gövdesi Giden iletiye kopyalanır. İleti daha sonra giden kanal gönderilir ve bu iletişim protokolüne/taşımasına özgü tüm üst bilgiler ve diğer zarf verileri oluşturulur ve eklenir.

Bu tür işleme adımları SOAP işleme davranışı belirtildiğinde gerçekleşir. Bu [\<soapProcessingExtension>](soapprocessing.md) davranış, yönlendirme hizmeti başlatıldığında tüm istemci (giden) uç noktalarına uygulanan bir uç nokta davranışıdır. Varsayılan olarak, [\<routing>](routing-of-servicebehavior.md) davranış [\<soapProcessingExtension>](soapprocessing.md) `processMessages` `true` her istemci uç noktası için olarak ayarlanmış yeni bir davranış oluşturur ve ekler. Yönlendirme hizmetinin anlayamadığı bir protokolüne sahipseniz veya varsayılan işleme davranışını geçersiz kılmak istiyorsanız, tüm yönlendirme hizmeti veya yalnızca belirli uç noktalar için SOAP işlemeyi devre dışı bırakabilirsiniz.  Tüm uç noktalarında tüm yönlendirme hizmeti için SOAP işlemeyi devre dışı bırakmak için `soapProcessing` [\<routing>](routing-of-servicebehavior.md) davranışın özniteliğini olarak ayarlayın `false` . Belirli bir uç nokta için SOAP işlemeyi devre dışı bırakmak için, bu davranışı kullanın ve `processMessages` özniteliğini olarak ayarlayın `false` , ardından bu davranışı varsayılan işleme kodunun çalıştırılmasını istemediğiniz uç noktaya ekleyin.  [\<routing>](routing-of-servicebehavior.md)Davranış yönlendirme hizmetini ayarlarken, zaten mevcut olduğundan, uç nokta davranışının yeniden uygulanması atlanacaktır.
