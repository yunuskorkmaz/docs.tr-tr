---
title: bypasslist için <remove> Öğesi (Ağ Ayarları)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove element, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
ms.openlocfilehash: a04cca3e57af5cc422776c5b2444a140e86f98b9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354264"
---
# <a name="remove-element-for-bypasslist-network-settings"></a>\<kaldırma > bypasslist (ağ ayarları) için

Bir IP adresi veya DNS adı proxy atlama listeden kaldırır.

\<Yapılandırma > \
\<System.NET > \
\<defaultProxy > \
\<bypasslist>\
\<kaldırma >

## <a name="syntax"></a>Sözdizimi

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|**Öznitelik**|**Açıklama**|
|-------------------|---------------------|
|`address`|Bir IP adresi veya DNS adını tanımlayan bir normal ifade.|

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|**Öğe**|**Açıklama**|
|-----------------|---------------------|
|[bypasslist](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|Bir proxy sunucu kullanmaması adresleri açıklayan normal bir ifade kümesi sağlar.|

## <a name="remarks"></a>Açıklamalar

`remove` Öğeyi normal ifadeler IP adresi veya DNS sunucu adları bir ara sunucu atlama adresleri listesinden kaldırır. Adresler, yapılandırma dosyasında ya da daha yüksek bir düzeyde yapılandırma hiyerarşideki daha önce tanımlanmadı.

Değeri `address` öznitelik, bir dizi IP adresi veya ana bilgisayar adları açıklayan bir normal ifade olmalıdır.

Normal ifadeler hakkında daha fazla bilgi için bkz. [.NET framework normal ifadelerinde](../../../../../docs/standard/base-types/regular-expressions.md).

## <a name="configuration-files"></a>Yapılandırma Dosyaları

Bu öğe, uygulama yapılandırma dosyası veya makine yapılandırma dosyası (Machine.config) kullanılabilir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, adventure works.com'u etki alanı için herhangi bir önceki tanım kaldırır ve sonra contoso.com etki alanına atlama listesine ekler.

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <bypasslist>
        <remove address="[a-z]+\.adventure-works\.com$" />
        <add address="[a-z]+\.contoso\.com$" />
      </bypasslist>
    </defaultProxy>
  </system.net>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [Ağ Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
