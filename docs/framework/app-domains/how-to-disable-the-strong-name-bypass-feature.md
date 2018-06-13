---
title: 'Nasıl yapılır: Tanımlayıcı Adlı Atlama Özelliğini Devre Dışı Bırakma'
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9604969ea073b07af0eca8d481f5459ee15d099
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742425"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a>Nasıl yapılır: Tanımlayıcı Adlı Atlama Özelliğini Devre Dışı Bırakma
İle .NET Framework sürüm 3.5 Service Pack 1 (SP1) başlayarak, tam güvene bir derleme yüklendiğinde güçlü ad imzaları doğrulanmaz <xref:System.AppDomain> varsayılan gibi nesne <xref:System.AppDomain> için `MyComputer` bölgesi. Bu özellik güçlü-adı olarak atlamak için adlandırılır. İçin tam güven ortamında, talep <xref:System.Security.Permissions.StrongNameIdentityPermission> imzalı için tam güven derlemeleri imzalarına bakılmaksızın her zaman başarılı. Ve bölgesi tam olarak güvenilir olmadığı için derleme tam olarak güvenilir olması gerektiğini yalnızca kısıtlamadır. Güçlü ad bu koşullarda belirleyici faktör olmadığından doğrulanması için için bir neden yoktur. Tanımlayıcı adlı imza doğrulaması atlayarak önemli ölçüde performans artışı sağlar.  
  
 Gecikme-imzalı değil ve hiçbir tam güvene yüklenen tüm tam güven derlemesi atlama özelliğini uygulandığı <xref:System.AppDomain> tarafından belirtilen dizinden kendi <xref:System.AppDomainSetup.ApplicationBase%2A> özelliği.  
  
 Kayıt defteri anahtarı değerini ayarlayarak bir bilgisayardaki tüm uygulamalar için atlama özelliğini geçersiz kılabilirsiniz. Uygulama yapılandırma dosyası kullanarak tek bir uygulama ayarı geçersiz kılabilirsiniz. Kayıt defteri anahtarı tarafından devre dışı bırakılırsa atlama özelliği tek bir uygulama için yeniden devreye sokmanız olamaz.  
  
 Atlama özelliğini geçersiz kıldığınızda, güçlü ad yalnızca doğruluğu doğrulanır. için işaretli bir <xref:System.Security.Permissions.StrongNameIdentityPermission>. Belirli bir güçlü ad doğrulamak istiyorsanız, o onay ayrı olarak yapmanız gerekir.  
  
> [!IMPORTANT]
>  Tanımlayıcı ad doğrulaması zorlama olanağı, aşağıdaki yordamda açıklandığı gibi bir kayıt defteri anahtarı bağlıdır. Bir uygulama bu kayıt defteri anahtarına erişmek için erişim denetim listesi (ACL) iznine sahip olmayan bir hesap altında çalışıyorsa verimsiz bir ayardır. Böylece tüm derlemeler için okunabilir ACL hakları bu anahtar için yapılandırılmış olan emin olmalısınız.  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-all-applications"></a>Tanımlayıcı adlı atlama özelliği tüm uygulamalar için devre dışı bırakmak için  
  
-   32-bit bilgisayarlarda, sistem kayıt defteri DWORD girdisi adlı 0 değerine sahip oluşturun `AllowStrongNameBypass` HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft altında\\. NETFramework anahtarı.  
  
-   64-bit bilgisayarlarda, sistem kayıt defteri DWORD girdisi adlı 0 değerine sahip oluşturun `AllowStrongNameBypass` HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft altında\\. NETFramework ve HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework anahtarları.  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-a-single-application"></a>Tanımlayıcı adlı atlama özelliği tek bir uygulama için devre dışı bırakmak için  
  
1.  Uygulama yapılandırma dosyası oluşturun veya açın.  
  
     Uygulama yapılandırma dosyaları bölümünde bu dosya hakkında daha fazla bilgi için bkz: [yapılandırma uygulamaları](../../../docs/framework/configure-apps/index.md).  
  
2.  Aşağıdaki girişi ekleyin:  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 Yapılandırma dosyası ayarı kaldırarak veya öznitelik "true" olarak ayarlayarak uygulamanın atlama özelliğini geri yükleyebilirsiniz.  
  
> [!NOTE]
>  Atlama özelliği bilgisayar için yalnızca etkinse, bir uygulama için tanımlayıcı ad doğrulama açıp kapatabilirsiniz. Atlama özelliğini bilgisayarı kapatılmış, tanımlayıcı adlar tüm uygulamalar için doğrulanır ve tek bir uygulama doğrulamasını atlayamazsınız.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sn.exe (Tanımlayıcı Ad Aracı)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [\<bypassTrustedAppStrongNames > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)  
 [Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
