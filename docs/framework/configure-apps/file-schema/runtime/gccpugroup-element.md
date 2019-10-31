---
title: <GCCpuGroup> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: 352890519c1a227d664d877c3123866e5e4e1657
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116840"
---
# <a name="gccpugroup-element"></a>\<GCCpuGroup > öğesi

Çöp toplamanın birden çok CPU grubunu destekleyip desteklemediğini belirtir.

[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp;&nbsp;&nbsp;&nbsp; **\<GCCpuGroup >**  

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

Bir bilgisayarda birden çok CPU grubu olduğunda ve sunucu çöp toplama etkin olduğunda (bkz. [\<gcServer >](gcserver-element.md) öğesi), bu ÖĞENIN tüm CPU gruplarında çöp toplamayı genişlettiği ve ve oluştururken tüm çekirdekleri hesaba ayırır Heap 'ler dengeleniyor.

> [!NOTE]
> Bu öğe yalnızca çöp toplama iş parçacıkları için geçerlidir. Çalışma zamanının tüm CPU gruplarında Kullanıcı iş parçacıklarını dağıtmasını sağlamak için, [\<Thread_UseAllCpuGroups >](thread-useallcpugroups-element.md) öğesini de etkinleştirmeniz gerekir.

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

- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
- [Eşzamanlı atık toplamayı devre dışı bırakmak için](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [İş istasyonu ve sunucu atık toplama](../../../../standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
