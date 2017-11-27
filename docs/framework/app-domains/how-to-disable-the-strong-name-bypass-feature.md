---
title: "Nasıl yapılır: Tanımlayıcı Adlı Atlama Özelliğini Devre Dışı Bırakma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
caps.latest.revision: "30"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fe694f9324a67e1ffa3eacf16cfbfcc266550693
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Sn.exe (tanımlayıcı ad aracı)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [\<bypassTrustedAppStrongNames > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)  
 [Oluşturma ve tanımlayıcı adlı derlemeler kullanma](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
