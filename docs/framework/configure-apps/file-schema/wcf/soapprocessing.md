---
title: <soapProcessing>
ms.date: 03/30/2017
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
ms.openlocfilehash: 0bedcec1a87f8384a89f5e5931c18ccebe87f07e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758021"
---
# <a name="soapprocessing"></a>\<soapProcessing >

Farklı bir bağlama türleri ve ileti sürümleri arasında iletileri hazırlamak için kullanılan istemci uç noktası davranışını tanımlar.

**\<sistemi. ServiceModel >**   
&nbsp;&nbsp;**\<davranışlar >**   
&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointBehaviors>**   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<davranışı >**   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing >**
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<soapProcessing processMessages="true|false" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler  
  
Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|                   | Açıklama |
| ----------------- | ----------- |
| `processMessages` | İletilerin SOAP ileti sürümleri arasında sıralanmış olup olmadığını belirten bir Boole değeri. |

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|     | Açıklama |
| --- | ----------- |
| [**\<davranışı >**](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) | Bir uç nokta davranışı belirtir. |

## <a name="remarks"></a>Açıklamalar

SOAP işleme iletisi sürümler arasında iletileri burada dönüştürülür işlemidir.

Windows Communication Foundation (WCF) yönlendirme hizmeti, iletileri bir protokolden dönüştürebilirsiniz. Gelen ve giden ileti sürümleri farklı ise doğru sürümünün yeni bir ileti oluşturulur. Bir ileti işleme <xref:System.ServiceModel.Channels.MessageVersion> diğerine gelen WCF iletisi ilgili üstbilgi ve gövde bölümünü içeren yeni bir WCF ileti oluşturularak gerçekleştirilir. Belirli adresleri olan veya bu anladım yönlendirici düzeyinde kullanılmaz yeni WCF ileti bir oluşumu sırasında bu üst bilgileri (söz konusu olduğunda üstbilgileri adresleme) farklı bir sürümü ya da bir parçası olarak işlenen olduğundan üst bilgileri istemci ile yönlendirici arasında iletişim.

Giden iletide bir üstbilgi olup yerleştirilir olsun veya olmasın, gelen kanal katmanını geçti olarak anlaşılmasını olarak işaretlendi tarafından belirlenir. (Gibi özel üst bilgiler) olarak anlaşılmamıştır üst bilgiler, kaldırılmaz ve bu nedenle yönlendirme hizmeti aracılığıyla Giden iletinin kopyalanan tarafından geçirin. Giden iletinin ileti gövdesini kopyalanır. İleti Giden kanal çıkış gönderilmesi, tüm üst bilgileri ve belirli diğer Zarf verileri bu iletişimi noktada, Protokolü/Aktarım oluşturulacak ve.

SOAP işleme davranışını belirtildiğinde bu tür işleme adımları gerçekleşir. Bu [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) yönlendirme hizmeti başlatıldığında, tüm istemci (giden) uç noktalar için uygulanan bir uç nokta davranışı bir davranıştır. Varsayılan, [ \<yönlendirme >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) davranışı oluşturur ve yeni bir ekler [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) davranışı ile `processMessages` kümesine `true` her İstemci uç noktası. Yönlendirme hizmeti değil anlamak veya davranış işleme Varsayılanı geçersiz kılmak istediğiniz bir protokol varsa, tüm yönlendirme hizmetini veya yalnızca belirli uç noktaları için işleme SOAP devre dışı bırakabilirsiniz.  SOAP tüm yönlendirme hizmeti tüm uç noktalarda işlemeyi devre dışı bırakmak için ayarlanmış `soapProcessing` özniteliği [ \<yönlendirme >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) davranışa `false`. Belirli bir uç nokta için işleme SOAP kapatmak için bu davranışı kullanmak ve ayarlamak kendi `processMessages` özniteliğini `false`, ardından bu davranışı çalışmak üzere kod işleme varsayılan istemediğiniz uç noktası ekleme.  Zaman [ \<yönlendirme >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) davranışını ayarlar yönlendirme hizmeti oluşturan, uç nokta davranışı bir zaten mevcut olduğundan yeniden uygulama atlar.
