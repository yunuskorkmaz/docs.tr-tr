---
title: 'Nasıl yapılır: tanımlayıcı adı atlama özelliğini devre dışı bırakma'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
ms.openlocfilehash: a4c4ae7ea61a659d3bede532da3c1bdaea448873
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141110"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a>Nasıl yapılır: tanımlayıcı adı atlama özelliğini devre dışı bırakma
.NET Framework sürüm 3,5 hizmet paketi 1 ' den (SP1) başlayarak, bir derleme bir tam güvenle <xref:System.AppDomain> nesnesine yüklendiğinde, `MyComputer` bölgesi için varsayılan <xref:System.AppDomain> gibi tanımlayıcı ad imzaları doğrulanmaz. Bu, tanımlayıcı ad atlama özelliği olarak adlandırılır. Tam güven ortamında, imzaları ne olursa olsun imzalı, tam güvenle derlemeler için <xref:System.Security.Permissions.StrongNameIdentityPermission> talepleri her zaman başarılı olur. Tek kısıtlama, kendi bölgesi tam güvenilir olduğu için derlemenin tam güvenilir olması gerekir. Tanımlayıcı ad bu koşullar altında bir belirleme faktörü olmadığından, bunun doğrulanması için bir neden yoktur. Tanımlayıcı ad imzalarının doğrulanmasını atlamak, önemli performans iyileştirmeleri sağlar.  
  
 Atlama özelliği, Gecikmeli imzalı olmayan ve <xref:System.AppDomainSetup.ApplicationBase%2A> özelliği tarafından belirtilen dizinden herhangi bir tam güvenle <xref:System.AppDomain> yüklenen tüm tam güven derlemeleri için geçerlidir.  
  
 Bir kayıt defteri anahtarı değeri ayarlayarak, bir bilgisayardaki tüm uygulamalar için atlama özelliğini geçersiz kılabilirsiniz. Bir uygulama yapılandırma dosyası kullanarak tek bir uygulama için ayarı geçersiz kılabilirsiniz. Kayıt defteri anahtarı tarafından devre dışı bırakılmışsa, tek bir uygulama için atlama özelliğini eski durumuna getiremezsiniz.  
  
 Atlama özelliğini geçersiz kıldığınızda, tanımlayıcı ad yalnızca doğruluk için onaylanır; <xref:System.Security.Permissions.StrongNameIdentityPermission>için denetlenmez. Belirli bir tanımlayıcı adı doğrulamak istiyorsanız, bu denetimi ayrı yapmanız gerekir.  
  
> [!IMPORTANT]
> Güçlü ad doğrulamasını zorlama özelliği, aşağıdaki yordamda açıklandığı gibi bir kayıt defteri anahtarına bağlıdır. Bir uygulama, bu kayıt defteri anahtarına erişim denetim listesi (ACL) iznine sahip olmayan bir hesap altında çalışıyorsa, ayar etkisiz olur. Tüm derlemeler için okunabilmesi için ACL haklarının bu anahtar için yapılandırıldığından emin olmanız gerekir.  
  
## <a name="disable-the-strong-name-bypass-feature-for-all-applications"></a>Tüm uygulamalar için tanımlayıcı adı atlama özelliğini devre dışı bırakma  
  
- 32 bit bilgisayarlarda, sistem kayıt defterinde, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\altında `AllowStrongNameBypass` adlı değeri 0 olan bir DWORD girişi oluşturun. NETFramework anahtarı.  
  
- 64 bit bilgisayarlarda, sistem kayıt defterinde, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\altında `AllowStrongNameBypass` adlı değeri 0 olan bir DWORD girişi oluşturun. NETFramework ve HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework anahtarları.  
  
## <a name="disable-the-strong-name-bypass-feature-for-a-single-application"></a>Tek bir uygulama için tanımlayıcı adı atlama özelliğini devre dışı bırakma  
  
1. Uygulama yapılandırma dosyasını açın veya oluşturun.  
  
    Bu dosya hakkında daha fazla bilgi için [uygulamaları yapılandırma](../../framework/configure-apps/index.md)konusunun uygulama yapılandırma dosyaları bölümüne bakın.  
  
2. Aşağıdaki girişi ekleyin:  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 Yapılandırma dosyası ayarını kaldırarak veya özniteliğini `true`olarak ayarlayarak, uygulamanın atlama özelliğini geri yükleyebilirsiniz.  
  
> [!NOTE]
> Yalnızca bilgisayar için atlama özelliği etkinse, bir uygulama için tanımlayıcı ad doğrulamayı açıp kapatabilirsiniz. Bilgisayar için atlama özelliği kapatılmışsa, tüm uygulamalar için tanımlayıcı adlar onaylanır ve tek bir uygulama için doğrulamayı atlayamazsınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sn.exe (Tanımlayıcı Ad Aracı)](../../framework/tools/sn-exe-strong-name-tool.md)
- [\<bypassTrustedAppStrongNames > öğesi](../../framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [Tanımlayıcı adlı derlemeler oluşturma ve kullanma](create-use-strong-named.md)
