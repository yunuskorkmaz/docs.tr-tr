---
title: 'Nasıl yapılır: Güçlü ad atlama özelliğini devre dışı'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
ms.openlocfilehash: a4c4ae7ea61a659d3bede532da3c1bdaea448873
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141110"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a>Nasıl yapılır: Güçlü ad atlama özelliğini devre dışı
.NET Framework sürümü 3.5 Service Pack 1 (SP1) ile başlayarak, bir derleme <xref:System.AppDomain> <xref:System.AppDomain> `MyComputer` bölge için varsayılan gibi tam güven nesnesine yüklendiğinde güçlü ad imzaları doğrulanmaz. Buna güçlü ad bypass özelliği denir. Tam güven ortamında, imzaları <xref:System.Security.Permissions.StrongNameIdentityPermission> ne olursa olsun imzalı, tam güven derlemeleri için her zaman başarılı talepler. Tek kısıtlama, kendi bölgesi tam olarak güvenilir olduğu için montaj tam olarak güvenilir olması gerektiğidir. Güçlü ad bu koşullar altında belirleyici bir faktör olmadığından, doğrulanması için bir neden yoktur. Güçlü ad imzalarının doğrulanmasını atlayarak önemli performans iyileştirmeleri sağlar.  
  
 Baypas özelliği, gecikme imzalı olmayan ve <xref:System.AppDomain> <xref:System.AppDomainSetup.ApplicationBase%2A> özelliği tarafından belirtilen dizinden tam güvene yüklenen herhangi bir tam güven derlemesi için geçerlidir.  
  
 Bir kayıt defteri anahtar değeri ayarlayarak bilgisayardaki tüm uygulamalar için atlama özelliğini geçersiz kılabilirsiniz. Bir uygulama yapılandırma dosyası kullanarak tek bir uygulama için ayarı geçersiz kılabilirsiniz. Kayıt defteri anahtarı tarafından devre dışı bırakılmışsa, tek bir uygulama için atlama özelliğini eski haline getiremezsiniz.  
  
 Atlama özelliğini geçersiz kaldığınızda, güçlü ad yalnızca doğruluk için doğrulanır; için <xref:System.Security.Permissions.StrongNameIdentityPermission>kontrol edilmez. Belirli bir güçlü adı onaylamak istiyorsanız, bu denetimi ayrı olarak gerçekleştirmeniz gerekir.  
  
> [!IMPORTANT]
> Güçlü ad doğrulamayı zorlama yeteneği, aşağıdaki yordamda açıklandığı gibi bir kayıt defteri anahtarına bağlıdır. Bir uygulama, kayıt defteri anahtarına erişmek için erişim denetim listesi (ACL) izni olmayan bir hesap altında çalışıyorsa, ayar etkisizdir. Tüm derlemeler için okunabilmesi için ACL haklarının bu anahtar için yapılandırıldığından emin olmalısınız.  
  
## <a name="disable-the-strong-name-bypass-feature-for-all-applications"></a>Tüm uygulamalar için güçlü ad atlama özelliğini devre dışı  
  
- 32 bit bilgisayarlarda, sistem kayıt defterinde, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft `AllowStrongNameBypass` \\altında 0 değerine sahip bir DWORD girişi oluşturun. NETFramework anahtarı.  
  
- 64 bit bilgisayarlarda, sistem kayıt defterinde, HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft `AllowStrongNameBypass` \\altında 0 değerine sahip bir DWORD girişi oluşturun. NETFramework ve HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework tuşları.  
  
## <a name="disable-the-strong-name-bypass-feature-for-a-single-application"></a>Tek bir uygulama için güçlü ad atlama özelliğini devre dışı  
  
1. Uygulama yapılandırma dosyasını açın veya oluşturun.  
  
    Bu dosya hakkında daha fazla bilgi [için, Uygulamaları Yapılandırma](../../framework/configure-apps/index.md)bölümündeki Uygulama Yapılandırma Dosyaları bölümüne bakın.  
  
2. Aşağıdaki girişi ekleyin:  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 Yapılandırma dosya ayarını kaldırarak veya özniteliği 'ne `true`ayarlayarak uygulamanın atlama özelliğini geri yükleyebilirsiniz.  
  
> [!NOTE]
> Yalnızca bilgisayar için atlama özelliği etkinse, bir uygulama için güçlü ad doğrulaması açıp kapatabilirsiniz. Atlama özelliği bilgisayar için kapatılmışsa, tüm uygulamalar için güçlü adlar doğrulanır ve tek bir uygulama için doğrulamayı atlayamazsınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sn.exe (Tanımlayıcı Ad Aracı)](../../framework/tools/sn-exe-strong-name-tool.md)
- [\<bypassTrustedAppStrongNames> öğesi](../../framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [Tanımlayıcı adlı derlemeler oluşturma ve kullanma](create-use-strong-named.md)
