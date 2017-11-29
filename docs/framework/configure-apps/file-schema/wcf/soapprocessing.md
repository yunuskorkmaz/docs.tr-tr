---
title: '&lt;soapProcessing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e53225399e3acba275d2d95533c4baad20386a4a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltsoapprocessinggt"></a>&lt;soapProcessing&gt;

Farklı bağlama türleri ve ileti sürümleri arasında iletileri sıralama için kullanılan istemci uç nokta davranışını tanımlar.

**\<Sistem. ServiceModel >**   
&nbsp;&nbsp;**\<davranışları >**   
&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointBehaviors >**   
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
| `processMessages` | İletileri SOAP iletisi sürümler arasında sıralanmış olup olmadığını belirten bir Boole değeri. |

### <a name="child-elements"></a>Alt öğeleri

Yok.

### <a name="parent-elements"></a>Üst öğeler

|     | Açıklama |
| --- | ----------- |
| [**\<davranışı >**](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) | Bir uç nokta davranışını belirtir. |

## <a name="remarks"></a>Açıklamalar

SOAP işleme iletileri ileti sürümleri arasında burada dönüştürülür işlemidir.

[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Yönlendirme hizmeti dönüştürebilir iletileri bir protokolünden diğerine. Gelen ve giden ileti sürümleri farklıysa, doğru sürümünün yeni bir ileti oluşturulur. İleti birinden işleme <!--zz <xref:System.ServiceModel.Channel.MessageVersion> --> `MessageVersion` başka bir yeni oluşturarak elde edilir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] gövde bölümü ve ilgili üstbilgi gelen içeren ileti [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] ileti. Adresleme için belirli olan veya, anladım yönlendirici düzeyinde kullanılmaz yeni WCF ileti oluşturma sırasında bu üstbilgileri ya da (söz konusu olduğunda üstbilgileri adresleme) farklı bir sürüm olması veya bir parçası olarak işlenen üstbilgileri yönlendirici ile istemci arasındaki iletişim.

Üstbilgi giden iletisinde olup bulunuyor olsun veya olmasın, gelen kanal katmanını geçti olarak anladım olarak işaretlendi tarafından belirlenir. (Özel üstbilgiler gibi) anlaşılmayan üstbilgileri kaldırılmıyor ve bu nedenle yönlendirme hizmeti aracılığıyla Giden iletiye kopyalanmasını tarafından geçirin. Giden iletinin ileti gövdesini kopyalanır. İleti Giden kanal çıkış gönderilir, tüm üstbilgiler ve belirli diğer Zarf verileri için iletişimin noktada, Protokolü/Aktarım oluşturulan eklendi ve.

SOAP işleme davranışını belirtildiğinde bu tür işleme adımları gerçekleşir. Bu [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) yönlendirme hizmeti başladığında, tüm (giden) istemci uç noktaları için uygulanan bir uç noktası davranışı bir davranıştır. Varsayılan, [ \<yönlendirme >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) davranışı oluşturur ve yeni bir iliştirir [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) davranışa `processMessages` kümesine `true` her İstemci uç noktası. Yönlendirme hizmeti değil anlamak veya davranış işleme varsayılan geçersiz kılma istediğiniz protokol varsa, tüm yönlendirme hizmeti veya yalnızca belirli uç noktaları için işleme SOAP devre dışı bırakabilirsiniz.  Tüm yönlendirme hizmeti tüm bitiş noktalarında işlemeyi SOAP devre dışı bırakmak için ayarlanmış `soapProcessing` özniteliği [ \<yönlendirme >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) davranışına `false`. Belirli bir uç nokta için işleme SOAP kapatmak için bu davranış kullanın ve ayarlayın, `processMessages` özniteliğini `false`, bu davranış, istediğiniz adresindeki çalıştırmak için kod işleme varsayılan uç nokta ekleme.  Zaman [ \<yönlendirme >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) davranışını ayarlar yönlendirme hizmeti, zaten bir tane olduğundan uç noktası davranışı yeniden uygulanması atlar.
