---
title: <GCCpuGroup> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102898"
---
# <a name="gccpugroup-element"></a>\<GCCpuGroup> Öğesi

Çöp toplamanın birden çok CPU grubunu destekleyip desteklemediğini belirtir.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**

## <a name="syntax"></a>Sözdizimi

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`enabled`|Gerekli öznitelik.<br /><br /> Çöp toplamanın birden çok CPU grubunu destekleyip desteklemediğini belirtir.|

## <a name="enabled-attribute"></a>etkin Öznitelik

|Değer|Açıklama|
|-----------|-----------------|
|`false`|Çöp toplama birden çok CPU grubunu desteklemiyor. Bu varsayılandır.|
|`true`|Çöp toplama, sunucu çöp toplama etkinse birden çok CPU grubunu destekler.|

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|

## <a name="remarks"></a>Açıklamalar

Bir bilgisayarda birden çok CPU grubu olduğunda ve sunucu çöp toplama özelliği etkin olduğunda (bkz. [\<gcServer>](gcserver-element.md) öğesi), bu öğenin tüm CPU gruplarında çöp toplamayı genişlettiğini ve Heap 'ler oluştururken ve bunları dengeleyerek tüm çekirdekleri hesaba getirecek şekilde etkinleştirir.

> [!NOTE]
> Bu öğe yalnızca çöp toplama iş parçacıkları için geçerlidir. Çalışma zamanının tüm CPU gruplarında Kullanıcı iş parçacıklarını dağıtmasını sağlamak için, öğesini de etkinleştirmeniz gerekir [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) .

## <a name="example"></a>Örnek

Aşağıdaki örnekte, birden çok CPU grubu için çöp toplamanın nasıl etkinleştirileceği gösterilmektedir.

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
- [Eşzamanlı atık toplamayı devre dışı bırak](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [İş istasyonu ve sunucu atık toplama](../../../../standard/garbage-collection/workstation-server-gc.md)
