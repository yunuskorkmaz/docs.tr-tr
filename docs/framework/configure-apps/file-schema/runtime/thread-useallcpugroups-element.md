---
title: <Thread_UseAllCpuGroups> Öğesi
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
ms.openlocfilehash: a3a612c0ffbcb211157b9623d298ce8ad7a13e94
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115404"
---
# <a name="thread_useallcpugroups-element"></a>\<Thread_UseAllCpuGroups> Öğesi

Çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtıp dağıtmadığını belirtir.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Thread_UseAllCpuGroups>**  

## <a name="syntax"></a>Sözdizimi

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`enabled`|Gerekli öznitelik.<br /><br /> Çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtıp dağıtmadığını belirtir.|

## <a name="enabled-attribute"></a>etkin Öznitelik

|Değer|Açıklama|
|-----------|-----------------|
|`false`|Çalışma zamanı, yönetilen iş parçacıklarını birden çok CPU grubu arasında dağıtmaz. Bu varsayılandır.|
|`true`|Çalışma zamanı, yönetilen iş parçacıklarını birden çok CPU grubuna dağıtır ve bilgisayarda birden çok CPU grubu varsa ve [\<GCCpuGroup>](gccpugroup-element.md) öğesi etkinse.|

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|

## <a name="remarks"></a>Açıklamalar

Bir bilgisayarda birden çok CPU grubu olduğunda, bu öğenin etkinleştirilmesi çalışma zamanının yönetilen iş parçacıklarını tüm CPU grupları arasında dağıtmasını sağlar. Bu özelliği kullanmak için [\<GCCpuGroup>](gccpugroup-element.md) çöp toplamayı tüm CPU gruplarına genişleten ve Heap 'ler oluştururken ve dengeleyerek tüm çekirdekleri hesaba götüren öğesini de etkinleştirmeniz gerekir. Öğesinin etkinleştirilmesi için [\<GCCpuGroup>](gccpugroup-element.md) öğesini etkinleştirmeniz gerekir [\<gcServer>](gcserver-element.md) . Bu öğeler etkinleştirilmemişse, `<Thread_UseAllCpuGroups>` öğesinin etkinleştirilmesi etkisizdir.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, birden çok CPU grubu için desteğin nasıl etkinleştirileceği gösterilmektedir.

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
- [\<GCCpuGroup>Dosyalarında](gccpugroup-element.md)
