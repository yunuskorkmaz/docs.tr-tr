---
description: Bir DotNet uygulamasına katıştırılmış Windows kaynaklarını denetlemek için C# derleyici seçenekleri.
title: C# derleyici seçenekleri-kaynak seçenekleri
ms.date: 03/12/2021
f1_keywords:
- cs.build.options
helpviewer_keywords:
- Win32Resource compiler option [C#]
- Win32Icon compiler option [C#]
- Win32Manifest compiler option [C#]
- NoWin32Manifest compiler option [C#]
- Resources compiler option [C#]
- LinkResources compiler option [C#]
ms.openlocfilehash: fe2da8cae67bc597d2b84a395861a0e4c32c9d72
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103482901"
---
# <a name="c-compiler-options-that-specify-resources"></a>Kaynakları belirten C# derleyici seçenekleri

Aşağıdaki seçenekler, C# derleyicisinin Win32 kaynaklarını nasıl oluşturduğunu veya içe aktaracağı denetler. Yeni MSBuild sözdizimi **kalın** olarak gösterilir. Eski *csc.exe* sözdizimi içinde gösterilir `code style` .

- **Win32Resource**  /  `-win32res` : bir Win32 kaynak dosyası (. res) belirtin.
- **Win32Icon**  /  `-win32icon` : belirtilen derleme dosyası veya dosyalarından meta verilere başvur.
- **Win32manifest**  /  `-win32manifest` : bir Win32 bildirim dosyası (. xml) belirtin.
- **Nowin32manifest**  /  `-nowin32manifest` : varsayılan Win32 bildirimini eklemeyin.
- **Kaynaklar**  /  `-resource` : belirtilen kaynağı katıştır (kısa biçim:/res).
- **LinkResources**  /  `-linkresources` : belirtilen kaynağı bu derlemeye bağla.

## <a name="win32resource"></a>Win32Resource

**Win32Resource** seçeneği, çıkış dosyasına bir Win32 kaynağı ekler.

```xml
<Win32Resource>filename</Win32Resource>
```

`filename` , çıkış dosyanıza eklemek istediğiniz kaynak dosyasıdır. Bir Win32 kaynağı, uygulamanızı dosya Gezgini 'nde tanımlamanızı sağlayacak sürüm veya bit eşlem (simge) bilgilerini içerebilir. Bu seçeneği belirtmezseniz, derleyici derleme sürümünü temel alan sürüm bilgilerini oluşturacaktır.

## <a name="win32icon"></a>Win32Icon

**Win32Icon** seçeneği çıkış dosyasına bir. ico dosyası ekler ve bu, çıktı dosyasına dosya Gezgini 'nde istenen görünümü verir.
  
```xml
<Win32Icon>filename</Win32Icon>
```

`filename` , çıkış dosyanıza eklemek istediğiniz *. ico* dosyasıdır. [Kaynak derleyicisi](/windows/desktop/menurc/resource-compiler)ile bir *. ico* dosyası oluşturulabilir. Visual C++ programı derlerken kaynak derleyicisi çağrılır; . *ico* dosyası *. RC* dosyasından oluşturulur.

## <a name="win32manifest"></a>Win32Manifest

Bir projenin Taşınabilir çalıştırılabilir (PE) dosyasına gömülecek Kullanıcı tanımlı bir Win32 uygulama bildirim dosyası belirtmek için **win32manifest** seçeneğini kullanın.

```xml
<Win32Manifest>filename</Win32Manifest>
```

`filename` , özel bildirim dosyasının adı ve konumudur. Varsayılan olarak, C# derleyicisi istenen "asInvoker" yürütme düzeyini belirten bir uygulama bildirimi katıştırır. Bildirimi, yürütülebilir dosyanın oluşturulduğu klasörde oluşturur. Örneğin, istenen "highestAvailable" veya "requireAdministrator" yürütme düzeyini belirtmek için özel bir bildirim sağlamak istiyorsanız, dosyanın adını belirtmek için bu seçeneği kullanın.

> [!NOTE]
> Bu seçenek ve **Win32Resources** seçeneği birbirini dışlıyor. Her iki seçeneği de aynı komut satırında kullanmayı denerseniz, bir derleme hatası alırsınız.

İstenen bir yürütme düzeyini belirten uygulama bildirimi olmayan bir uygulama, Windows 'daki Kullanıcı hesabı denetimi özelliği altında dosya ve kayıt defteri sanallaştırmaya tabidir. Daha fazla bilgi için bkz. [Kullanıcı hesabı denetimi](/windows/access-protection/user-account-control/user-account-control-overview).

Uygulamanız, bu koşullardan biri doğru olduğunda sanallaştırmaya tabi olacaktır:
  
- **Nowin32manifest** seçeneğini kullanın ve **Win32Resource** seçeneğini kullanarak sonraki bir derleme adımında veya Windows kaynak (*. res*) dosyasının bir parçası olarak bir bildirim sağlamamazsınız.
- İstenen yürütme düzeyini belirtmeyen özel bir bildirim sağlarsınız.

Visual Studio varsayılan bir *. manifest* dosyası oluşturur ve yürütülebilir dosyanın yanı sıra hata ayıklama ve sürüm dizinlerinde depolar. Herhangi bir metin düzenleyicisinde bir tane oluşturarak ve sonra dosyayı projeye ekleyerek özel bir bildirim ekleyebilirsiniz. Ya da **Çözüm Gezgini**' de **Proje** simgesine sağ tıklayıp **Yeni öğe Ekle**' yi ve ardından **uygulama bildirim dosyası**' nı seçin. Yeni veya mevcut bildirim dosyanızı ekledikten sonra, **bildirim** açılan listesinde görünür. Daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).

Uygulama bildirimini özel derleme sonrası bir adım olarak veya **nowin32manifest** seçeneğini kullanarak bir Win32 kaynak dosyasının parçası olarak sağlayabilirsiniz. Uygulamanızın Windows Vista 'da dosya veya kayıt defteri sanallaştırmaya tabi olmasını istiyorsanız bu seçeneği kullanın.
  
## <a name="nowin32manifest"></a>NoWin32Manifest

Derleyicinin herhangi bir uygulama bildirimini yürütülebilir dosyaya katıştırmamasını sağlamak için **nowin32manifest** seçeneğini kullanın.

```xml  
<NoWin32Manifest />
```

Bu seçenek kullanıldığında, bir Win32 kaynak dosyasında veya sonraki bir derleme adımı sırasında uygulama bildirimi belirtmediğiniz müddetçe uygulama Windows Vista 'da sanallaştırmaya tabi olacaktır.

Visual Studio 'da, **bildirim** açılan listesinde **bildirim olmadan uygulama oluştur** seçeneğini belirleyerek **uygulama özelliği** sayfasında bu seçeneği ayarlayın. Daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).

## <a name="resources"></a>Kaynaklar

Belirtilen kaynağı çıkış dosyasına katıştırır.

```xml
<Resources Include=filename>
  <LogicalName>identifier</LogicalName>
  <Access>accessibility-modifier</Access>
</Resources>
```

`filename` , çıkış dosyasına eklemek istediğiniz .NET kaynak dosyasıdır. `identifier` (isteğe bağlı) kaynağın mantıksal adıdır; kaynağı yüklemek için kullanılan ad. Varsayılan değer, dosyanın adıdır. `accessibility-modifier` (isteğe bağlı) kaynağın erişilebilirliği: public veya Private. Varsayılan değer geneldir. Varsayılan olarak, kaynaklar C# derleyicisi kullanılarak oluşturulduğunda derlemede ortaktır. Kaynakları özel hale getirmek için `private` erişilebilirlik değiştiricisi olarak belirtin. Veya dışında başka bir erişilebilirliği `public` olamaz `private` . `filename`Örneğin, [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında oluşturulmuş bir .net kaynak dosyası ise, <xref:System.Resources> ad alanındaki üyelerle erişilebilir. Daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Diğer tüm kaynaklar için, `GetManifestResource` <xref:System.Reflection.Assembly> çalışma zamanında kaynağa erişmek üzere sınıfındaki yöntemleri kullanın. Çıkış dosyasındaki kaynakların sırası proje dosyasında belirtilen sırada belirlenir.  
  
## <a name="linkresources"></a>LinkResources

Çıkış dosyasında .NET kaynağına bir bağlantı oluşturur. Kaynak dosyası çıkış dosyasına eklenmez. **LinkResources** , çıkış dosyasına bir kaynak dosyası eklemek için **kaynak** seçeneğinden farklıdır.

```xml
<LinkResources Include=filename>
  <LogicalName>identifier</LogicalName>
  <Access>accessibility-modifier</Access>
</LinkResources>
```

`filename` , derlemeden bağlamak istediğiniz .NET kaynak dosyasıdır. `identifier` (isteğe bağlı) kaynağın mantıksal adıdır; kaynağı yüklemek için kullanılan ad. Varsayılan değer, dosyanın adıdır. `accessibility-modifier` (isteğe bağlı) kaynağın erişilebilirliği: public veya Private. Varsayılan değer geneldir. Varsayılan olarak, bağlı kaynaklar C# derleyicisi ile oluşturulduklarında derlemede ortaktır. Kaynakları özel hale getirmek için `private` erişilebilirlik değiştiricisi olarak belirtin. Veya dışında başka bir değiştirici `public` `private` kullanılamaz. `filename`Örneğin, [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) veya geliştirme ortamında oluşturulmuş bir .net kaynak dosyası ise, <xref:System.Resources> ad alanındaki üyelerle erişilebilir. Daha fazla bilgi için bkz. <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Diğer tüm kaynaklar için, `GetManifestResource` <xref:System.Reflection.Assembly> çalışma zamanında kaynağa erişmek üzere sınıfındaki yöntemleri kullanın. İçinde belirtilen dosya `filename` herhangi bir biçimde olabilir. Örneğin, genel derleme önbelleğine yüklenebilmesi ve derlemedeki yönetilen koddan erişilebilmesi için derlemenin yerel bir DLL parçası yapmak isteyebilirsiniz. Derleme bağlayıcıda aynı şeyi yapabilirsiniz. Daha fazla bilgi için bkz. [Al.exe (bütünleştirilmiş kod bağlayıcı)](../../../framework/tools/al-exe-assembly-linker.md) ve [derlemeler ve genel derleme önbelleği ile çalışma](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).
