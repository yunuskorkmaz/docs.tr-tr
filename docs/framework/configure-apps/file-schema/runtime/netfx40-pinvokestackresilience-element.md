---
title: <NetFx40_PInvokeStackResilience> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
ms.openlocfilehash: 86f50aafe0b21d5080288e09ac7118ca1e4c939a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73116153"
---
# <a name="netfx40_pinvokestackresilience-element"></a>\<NetFx40_PInvokeStackResilience> Öğesi

Çalışma zamanının, yönetilen ve yönetilmeyen kod arasındaki yavaş geçişlerin maliyetinde, çalışma zamanında hatalı platform çağırma bildirimlerini otomatik olarak düzeltilmediğini belirtir.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_PInvokeStackResilience>**  

## <a name="syntax"></a>Sözdizimi

```xml
<NetFx40_PInvokeStackResilience  enabled="1|0"/>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanının yanlış platform çağırma bildirimleri algıladığını ve 32-bit platformlarda çalışma zamanında yığını otomatik olarak düzeltmediğini belirtir.|

## <a name="enabled-attribute"></a>etkin Öznitelik

|Değer|Açıklama|
|-----------|-----------------|
|`0`|Çalışma zamanı, yanlış platform çağırma bildirimlerini algılamadığında ve gideremeyecek .NET Framework 4 ' te tanıtılan daha hızlı birlikte çalışma hazırlama mimarisini kullanır. Bu varsayılandır.|
|`1`|Çalışma zamanı, hatalı platform çağırma bildirimlerini algılayan ve giderecek daha yavaş geçişler kullanır.|

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|

## <a name="remarks"></a>Açıklamalar

Bu öğe, yanlış platform çağırma bildirimlerine karşı çalışma zamanı esnekliği için daha hızlı birlikte çalışma sıralaması sunmanızı sağlar.

.NET Framework 4 ' ten itibaren, kolaylaştırılmış bir birlikte çalışma hazırlama mimarisi yönetilen koddan yönetilmeyen koda yapılan geçişler için önemli bir performans geliştirmesi sağlar. .NET Framework önceki sürümlerinde, sıralama katmanı 32-bit platformlarda hatalı platform çağırma bildirimleri algıladı ve yığını otomatik olarak düzeltti. Yeni sıralama mimarisi bu adımı ortadan kaldırır. Sonuç olarak, geçişler çok hızlıdır, ancak yanlış platform çağırma bildirimi program hatasına neden olabilir.

Geliştirme sırasında yanlış bildirimleri algılamaya kolay hale getirmek için, Visual Studio hata ayıklama deneyimi geliştirilmiştir. [PInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) yönetilen hata ayıklama Yardımcısı (MDA), uygulamanız, ekli hata ayıklayıcı ile çalışırken hatalı platform çağırma bildirimlerini size bildirir.

Uygulamanızın, yeniden derleyemediği ve yanlış platform çağırma bildirimlerine sahip olan bileşenleri kullandığı senaryolara yönelik senaryolar için `NetFx40_PInvokeStackResilience` öğesini kullanabilirsiniz. Bu öğeyi, daha `enabled="1"` düşük geçişlerin maliyetinde, .NET Framework önceki sürümlerinin davranışıyla birlikte bir uyumluluk moduna ekleyerek uygulama yapılandırma dosyanıza ekleyin. Önceki .NET Framework sürümleriyle derlenen derlemeler otomatik olarak bu uyumluluk moduna alınır ve bu öğeye gerek kalmaz.

## <a name="configuration-file"></a>Yapılandırma Dosyası

Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, yönetilen ve yönetilmeyen kod arasındaki yavaş geçişlerin maliyetinde, bir uygulamanın yanlış platform çağırma bildirimlerine karşı artan esnekliği nasıl ekleneceğini gösterir.

```xml
<configuration>
   <runtime>
      <NetFx40_PInvokeStackResilience enabled="1"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
- [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md)
