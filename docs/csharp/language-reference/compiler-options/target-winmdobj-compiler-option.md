---
title: '-target: winmdobj (C# Derleyici Seçenekleri)'
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: 38d0dedbca56475d4f2561c99e8b29e01e9d7a90
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43740928"
---
# <a name="-targetwinmdobj-c-compiler-options"></a>-target: winmdobj (C# Derleyici Seçenekleri)
Kullanırsanız **-target: winmdobj** derleyici seçeneği, derleyicinin bir Windows çalışma zamanı (.winmd) ikili dosyasına dönüştürebileceğiniz bir ara .winmdobj dosyası oluşturur. .Winmd dosyası yönetilen dil programlarının yanı sıra, JavaScript ve C++ programları tarafından ardından tarafından kullanılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a>Açıklamalar  
 **Winmdobj** sinyalleri bir ara modülün gerekli olduğunu ayarı. Yanıt olarak, Visual Studio C# sınıf kitaplığını bir .winmdobj dosyası olarak derler. .Winmdobj dosyası daha sonra doldurularak <xref:Microsoft.Build.Tasks.WinMDExp> dışa aktarma aracı bir Windows meta veri (.winmd) dosyası. .Winmd dosyası, kod özgün kitaplık ve Windows çalışma zamanı ve JavaScript veya C++ tarafından kullanılan WinMD meta verilerini içerir.  
  
 Kullanılarak derlenmiş bir dosya çıktısı **-target: winmdobj** derleyici seçeneği, giriş olarak yalnızca WimMDExp verme aracı için kullanılmak üzere tasarlanmıştır; .winmdobj dosyasının kendisine doğrudan başvuru yapılmaz.  
  
 Kullanmadığınız sürece [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) seçeneği, çıkış dosyası adı ilk giriş dosyasının adını alır. A [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi gerekli değildir.  
  
 Belirtirseniz - target: winmdobj seçeneğini bir komut isteminde, sonraki kadar tüm dosyaları **-out** veya [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) seçeneği, Windows programı oluşturmak için kullanılır.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a>Bu derleyici seçeneğini Windows Mağazası uygulaması için Visual Studio IDE'de ayarlamak için  
  
1.  İçinde **Çözüm Gezgini**, projeniz için kısayol menüsünü açın ve ardından **özellikleri**.  
  
2.  Seçin **uygulama** sekmesi.  
  
3.  İçinde **çıkış türü** listesinde **WinMD dosyası**.  
  
     **WinMD dosyası** yalnızca seçeneğin kullanılabilir [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] uygulama şablonları.  
  
 Bu derleyici seçeneğini program üzerinden ayarlamak hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut `filename.cs` bir ara .winmdobj dosyasına.  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [-target (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)
