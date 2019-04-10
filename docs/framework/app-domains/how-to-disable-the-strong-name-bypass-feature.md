---
title: 'Nasıl yapılır: Tanımlayıcı Adlı Atlama Özelliğini Devre Dışı Bırakma'
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86fc35ae20211bd32a21d60b7313074361aef671
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296179"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a>Nasıl yapılır: Tanımlayıcı Adlı Atlama Özelliğini Devre Dışı Bırakma
İle .NET Framework sürüm 3.5 Service Pack 1 (SP1) başlayarak, tam güvene bir derleme yüklendiğinde tanımlayıcı ad imzaları doğrulanmaz <xref:System.AppDomain> gibi varsayılan nesne <xref:System.AppDomain> için `MyComputer` bölge. Bu atlama özelliğini tanımlayıcı ad adlandırılır. İçin tam güven ortamında, talepleri <xref:System.Security.Permissions.StrongNameIdentityPermission> imzalı için tam güven derlemeleri imzalarına bağımsız olarak her zaman başarılı. Tek kısıtlama, kendi bölgesine tam güvenilir olduğundan derleme tam güvenilir olması gerekliliğidir. Tanımlayıcı adı bir faktör Bu koşullar altında olmadığı için bunu doğrulanması için bir neden yoktur. Tanımlayıcı ad imzası doğrulama atlama önemli performans geliştirmeleri sunar.  
  
 Bu gecikme-imzalı değil ve bir tam güvene yüklenen herhangi bir tam güven derleme atlama özelliğini uygular <xref:System.AppDomain> tarafından belirtilen dizinden kendi <xref:System.AppDomainSetup.ApplicationBase%2A> özelliği.  
  
 Bir kayıt defteri anahtarı değerini ayarlayarak bir bilgisayarda tüm uygulamalar için atlama özelliğini geçersiz kılabilirsiniz. Uygulama yapılandırma dosyası kullanarak tek bir uygulama ayarı geçersiz kılabilirsiniz. Kayıt defteri anahtarı tarafından devre dışı bırakılırsa atlama özelliği tek bir uygulama için yeniden devreye sokmanız olamaz.  
  
 Atlama özelliğini geçersiz kıldığınızda, tanımlayıcı ad doğruluğu yalnızca doğrulanır. için işaretli bir <xref:System.Security.Permissions.StrongNameIdentityPermission>. Belirli bir tanımlayıcı ad doğrulamak istiyorsanız bu onay ayrı olarak yapmanız gerekir.  
  
> [!IMPORTANT]
>  Tanımlayıcı ad doğrulama zorlama olanağı, aşağıdaki yordamda açıklandığı gibi bir kayıt defteri anahtarı bağlıdır. Bir uygulama bu kayıt defteri anahtarına erişim için erişim denetim listesi (ACL) iznine sahip olmayan bir hesap altında çalışıyorsa, verimsiz bir ayardır. Böylece tüm derlemeler için okunabilir ACL hakları bu anahtar için yapılandırıldığından emin olmanız gerekir.  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-all-applications"></a>Tanımlayıcı ad atlama özelliği tüm uygulamalar için devre dışı bırakmak için  
  
-   32-bit bilgisayarlarda, sistem kayıt defterinde DWORD girişini adlı 0 değeri ile oluşturma `AllowStrongNameBypass` HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft altında\\. NETFramework anahtarı.  
  
-   64-bit bilgisayarlarda, sistem kayıt defterinde DWORD girişini adlı 0 değeri ile oluşturma `AllowStrongNameBypass` HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft altında\\. NETFramework ve HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework anahtarları.  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-a-single-application"></a>Tanımlayıcı ad atlama özelliği tek bir uygulama için devre dışı bırakmak için  
  
1. Uygulama yapılandırma dosyasını oluşturun veya açın.  
  
     Uygulama yapılandırma dosyaları bölümünde bu dosya hakkında daha fazla bilgi için bkz. [yapılandırma uygulamaları](../../../docs/framework/configure-apps/index.md).  
  
2. Şu girişi ekleyin:  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 Yapılandırma dosyası ayarı kaldırarak veya öznitelik "true" ayarını, uygulama için atlama özelliğini geri yükleyebilirsiniz.  
  
> [!NOTE]
>  Yalnızca bilgisayar için atlama özelliği etkinse, bir uygulama için tanımlayıcı ad doğrulama açıp kapatabilirsiniz. Atlama özelliği, bilgisayarı kapatılmış, tüm uygulamalar için güçlü adlar doğrulanır ve tek bir uygulama için doğrulamayı atlayamazsınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sn.exe (Tanımlayıcı Ad Aracı)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [\<bypassTrustedAppStrongNames > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [Tanımlayıcı Adlı Derlemeler Oluşturma ve Kullanma](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
