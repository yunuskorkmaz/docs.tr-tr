---
title: <bypassTrustedAppStrongNames> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
ms.openlocfilehash: 96361a6742d1d2f76cb237344189d3277d7c8069
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739089"
---
# <a name="bypasstrustedappstrongnames-element"></a>\<bypassTrustedAppStrongNames> Öğesi

Tam güvenle yüklenmiş olan tam güven derlemelerindeki tanımlayıcı adların doğrulanmasının atlanıp atlanmayacağını belirtir <xref:System.AppDomain> .

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<bypassTrustedAppStrongNames>**

## <a name="syntax"></a>Sözdizimi

```xml
<bypassTrustedAppStrongNames
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`enabled`|Gerekli öznitelik.<br /><br /> Tam güven derlemeleri için tanımlayıcı adların doğrulanmasını önleyen atlama özelliğinin etkinleştirilip etkinleştirilmeyeceğini belirtir. Bu özellik etkinleştirildiğinde, derleme yüklendiğinde tanımlayıcı adlar doğruluk açısından doğrulanmaz. Varsayılan değer: `true`.|

## <a name="enabled-attribute"></a>etkin Öznitelik

|Değer|Açıklama|
|-----------|-----------------|
|`true`|Derlemeler tam güvenle yüklendiğinde, tam güven derlemelerindeki tanımlayıcı ad imzaları doğrulanmaz <xref:System.AppDomain> . Bu varsayılandır.|
|`false`|Tam güven derlemelerindeki tanımlayıcı ad imzaları, derlemeler tam güvenle yüklendiğinde onaylanır <xref:System.AppDomain> . Tanımlayıcı ad imzası yalnızca imza doğruluğu için denetlenir; bir eşleşme için başka bir tanımlayıcı adla karşılaştırılmaz.|

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|

## <a name="remarks"></a>Açıklamalar

Tanımlayıcı adı atlama özelliği, tam güven derlemelerinin tanımlayıcı ad imzası doğrulamasının yükünü önler.

Atlama özelliği, bir tanımlayıcı ad ile imzalanmış ve aşağıdaki özelliklere sahip olan her derleme için geçerlidir:

- Kanıt olmadan tamamen güvenilir <xref:System.Security.Policy.StrongName> (örneğin, `MyComputer` bölge kanıtları vardır).

- Tam güvenilir bir şekilde yüklendi <xref:System.AppDomain> .

- Özelliği altında bir konumdan yüklendi <xref:System.AppDomainSetup.ApplicationBase%2A> <xref:System.AppDomain> .

- Gecikmeli imza değildir.

> [!NOTE]
> Bir kayıt defteri anahtarı kullanılarak bilgisayardaki tüm uygulamalar için atlama özelliği kapatılmışsa, bu yapılandırma dosyası ayarının etkisi yoktur. Daha fazla bilgi için bkz. [nasıl yapılır: güçlü adı atlama özelliğini devre dışı bırakma](../../../../standard/assembly/disable-strong-name-bypass-feature.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, tam güven derlemelerinde tanımlayıcı ad imzasını doğrulayan davranışın nasıl yapılacağını gösterir.

```xml
<configuration>
   <runtime>
      <bypassTrustedAppStrongNames enabled="false"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
- [Nasıl yapılır: tanımlayıcı adı atlama özelliğini devre dışı bırakma](../../../../standard/assembly/disable-strong-name-bypass-feature.md)
