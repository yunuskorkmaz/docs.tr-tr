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
ms.openlocfilehash: 97b49a8a520d6a4f72945366874991d2deb18710
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697902"
---
# <a name="remove-element-for-bypasslist-network-settings"></a>BypassList için \<remove > öğesi (ağ ayarları)

Proxy atlama listesinden bir IP adresi veya DNS adı kaldırır.

[ **\<Yapılandırma >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<bypasslist >** ](bypasslist-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<remove >**  

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
|`address`|IP adresini veya DNS adını tanımlayan bir normal ifade.|

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|**Öğe**|**Açıklama**|
|-----------------|---------------------|
|[BypassList](bypasslist-element-network-settings.md)|Proxy kullanmayan adresleri tanımlayan normal ifadeler kümesi sağlar.|

## <a name="remarks"></a>Açıklamalar

@No__t-0 öğesi, IP adreslerini veya DNS sunucu adlarını tanımlayan normal ifadeleri, bir proxy sunucusunu atlayan adresler listesinden kaldırır. Adresler yapılandırma hiyerarşisinde daha önce veya yapılandırma hiyerarşisinde daha yüksek bir düzeyde tanımlandı.

@No__t-0 özniteliğinin değeri bir IP adresi veya ana bilgisayar adı kümesini açıklayan bir normal ifade olmalıdır.

Normal ifadeler hakkında daha fazla bilgi için bkz. [Normal ifadeleri .NET Framework](../../../../standard/base-types/regular-expressions.md).

## <a name="configuration-files"></a>Yapılandırma Dosyaları

Bu öğe, uygulama yapılandırma dosyasında veya makine yapılandırma dosyasında (Machine. config) kullanılabilir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, adventure-works.com etki alanı için önceki tüm tanımları kaldırır ve ardından contoso.com etki alanını atlama listesine ekler.

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
- [Ağ Ayarları Şeması](index.md)
