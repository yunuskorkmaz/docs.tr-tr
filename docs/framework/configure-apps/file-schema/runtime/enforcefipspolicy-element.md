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
ms.openlocfilehash: 9040bf2548964cf6df5f4fd87ee9f6d979c7df1e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746221"
---
# <a name="ltenforcefipspolicygt-element"></a>&lt;Enforcefıpspolicy&gt; öğesi
Şifreleme algoritmaları Federal Bilgi işleme standartları (FIPS ile) uymalıdır bir bilgisayar yapılandırmasını gereksinim zorlanıp zorlanmayacağını belirtir.  
  
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
|Etkin|Gerekli öznitelik.<br /><br /> Şifreleme algoritmaları FIPS ile uyumlu bir bilgisayar yapılandırma gereksinim zorlama etkinleştirilip etkinleştirilmeyeceğini belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`true`|Bu gereksinim, bilgisayarınızı FIPS uyumlu olacak şekilde şifreleme algoritmaları gerektirecek şekilde yapılandırılmışsa, zorlanır. Sınıf oluşturucuları FIPS ile uyumlu olmayan bir algoritma uyguluyorsa veya `Create` o bilgisayarda çalıştırdığınızda bu sınıf için yöntemleri throw özel durumları. Bu varsayılandır.|  
|`false`|Uygulama tarafından kullanılan şifreleme algoritmalarını bağımsız olarak bilgisayar yapılandırması FIPS ile uyumlu olmasını gerekli değildir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework 2.0 ile başlayarak, şifreleme algoritmaları uygulayan sınıflar oluşturulmasını bilgisayarı yapılandırma tarafından denetlenir. Bilgisayar algoritmaları FIPS ile uyumlu olmasını gerektirecek şekilde yapılandırılmış ve bir sınıf FIPS ile uyumlu olmayan bir algoritma uygular, bu sınıfın örneğini oluşturma girişimi herhangi bir özel durum oluşturur. Oluşturucular throw bir <xref:System.InvalidOperationException> özel durumu ve `Create` yöntemleri throw bir <xref:System.Reflection.TargetInvocationException> özel durum ile bir iç <xref:System.InvalidOperationException> özel durum.  
  
 Uygulamanız, yapılandırmaları FIPS ile uyumlu olmasını gerektir bilgisayarlarda çalışan ve uygulamanızın FIPS ile uyumlu olmayan bir algoritma kullanıyorsa, bu öğe, yapılandırma dosyanızda gelen ortak dil çalışma zamanı (CLR) önlemek için kullanabilirsiniz FIPS uyumluluk zorlama. Bu öğe sunulmuştur [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, FIPS uyumluluğu zorlamayı CLR önlemek gösterilmiştir.  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Şifreleme Modeli](../../../../../docs/standard/security/cryptography-model.md)
