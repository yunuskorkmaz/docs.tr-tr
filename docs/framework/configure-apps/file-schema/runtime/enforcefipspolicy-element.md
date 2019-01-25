---
title: '&lt;Enforcefıpspolicy&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 990add41d5f48da19f6bc20e4bbff19f36132df6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54742113"
---
# <a name="ltenforcefipspolicygt-element"></a>&lt;Enforcefıpspolicy&gt; öğesi
Şifreleme algoritmaları Federal Bilgi işleme standartları (FIPS ile) uyması gereken bir bilgisayar yapılandırma gereksinimini zorlanıp zorlanmayacağını belirtir.  
  
 \<Yapılandırma > öğesi  
\<çalışma zamanı > öğesi  
\<Enforcefıpspolicy > öğesi  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|Etkin|Gerekli öznitelik.<br /><br /> Şifreleme algoritması FIPS ile uyumlu bir bilgisayar yapılandırma gereksinimini uygulanması etkinleştirilip etkinleştirilmeyeceğini belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`true`|Bilgisayarınız, şifreleme algoritmaları FIPS uyumlu olmasını gerektirecek şekilde yapılandırılmışsa, bu gereksinimi zorunlu tutulur. Bir sınıf oluşturucuları FIPS ile uyumlu değil bir algoritma uyguluyorsa veya `Create` yöntemleri o sınıf için o bilgisayarda çalıştırdığınızda özel durum throw. Bu varsayılandır.|  
|`false`|Uygulama tarafından kullanılan şifreleme algoritmaları, bilgisayar yapılandırması ne olursa olsun, FIPS uyumlu olmasını gerekli değildir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Şifreleme algoritmalarını uygulayan sınıflar oluşturma, .NET Framework 2.0 ile başlayarak, bilgisayar yapılandırması tarafından denetlenir. Bilgisayar algoritmaları FIPS ile uyumlu olmasını gerektirecek şekilde yapılandırılmış ve bir sınıf FIPS ile uyumlu değil bir algoritma uygular, bu sınıfın bir örneğini oluşturmak için her türlü girişim, özel durum oluşturur. Throw oluşturucular bir <xref:System.InvalidOperationException> özel durumu ve `Create` yöntemleri throw bir <xref:System.Reflection.TargetInvocationException> özel durumla bir iç <xref:System.InvalidOperationException> özel durum.  
  
 FIPS uyumluluğu olan yapılandırmalar gerektirir bilgisayarlarda uygulamanızın çalıştığı ve uygulamanızı FIPS ile uyumlu değil bir algoritma kullanır, bu öğe yapılandırma dosyanızda gelen ortak dil çalışma zamanı (CLR) önlemek için kullanabilirsiniz FIPS uyumluluğunu zorlama. Bu öğe de sunulan [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, FIPS uyumluluğu zorlama gelen CLR önlemek gösterilmektedir.  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Şifreleme Modeli](../../../../../docs/standard/security/cryptography-model.md)
