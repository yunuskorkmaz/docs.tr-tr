---
title: <GCCpuGroup> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102898"
---
# <a name="gccpugroup-element"></a>\<GCCpuGroup> Elemanı

Çöp toplamanın birden çok CPU gruplarını destekleyip desteklemediğini belirtir.

[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)\
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
|`enabled`|Gerekli öznitelik.<br /><br /> Çöp toplamanın birden çok CPU gruplarını destekleyip desteklemediğini belirtir.|

## <a name="enabled-attribute"></a>etkin Öznitelik

|Değer|Açıklama|
|-----------|-----------------|
|`false`|Çöp toplama birden çok CPU gruplarını desteklemez. Bu varsayılandır.|
|`true`|Sunucu çöp toplama etkinse, çöp toplama birden çok CPU gruplarını destekler.|

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|

## <a name="remarks"></a>Açıklamalar

Bir bilgisayarda birden çok CPU grubu olduğunda ve sunucu çöp toplama etkinleştirildiğinde [ \<(gcServer>](gcserver-element.md) öğesine bakın), bu öğenin tüm CPU gruplarında çöp toplamayı genişletmesini ve yığınoluştururken ve dengeleme yaparken tüm çekirdekleri hesaba katmasını sağlar.

> [!NOTE]
> Bu öğe yalnızca çöp toplama iş parçacıkları için geçerlidir. Kullanıcı iş parçacıklarını tüm CPU gruplarına dağıtmak için çalışma süresini etkinleştirmek için [ \<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) öğesini de etkinleştirmeniz gerekir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, birden çok CPU grubu için çöp toplamanın nasıl etkinleştirilen gösterilmektedir.

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
- [Yapılandırma Dosya Şema](../index.md)
- [Eşzamanlı çöp toplamayı devre dışı](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [İş istasyonu ve sunucu çöp toplama](../../../../standard/garbage-collection/workstation-server-gc.md)
