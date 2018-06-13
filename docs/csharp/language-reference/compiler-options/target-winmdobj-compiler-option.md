---
title: '-target: winmdobj (C# Derleyici Seçenekleri)'
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: b0b1ec0bed174484e9ed7b9ecddbe82b0c705325
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218664"
---
# <a name="-targetwinmdobj-c-compiler-options"></a>-target: winmdobj (C# Derleyici Seçenekleri)
Kullanırsanız **-target: winmdobj** derleyici seçeneği derleyici Windows çalışma zamanı ikili (.winmd) dosyasına dönüştüren bir ara .winmdobj dosyası oluşturur. .Winmd dosya yönetilen dil programlar yanı sıra, JavaScript ve C++ programlarla sonra kullanılabilecek.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a>Açıklamalar  
 **Winmdobj** Ara bir modül gerekli olduğunu derleyici sinyalleri ayarlama. Yanıt olarak, Visual Studio C# sınıf kitaplığı .winmdobj dosyası olarak derler. .Winmdobj dosya sonra aracılığıyla Sat <xref:Microsoft.Build.Tasks.WinMDExp> dışa aktarma Windows (.winmd) meta veri dosyası üretmek için aracı. .Winmd dosyası kodu özgün kitaplık ve JavaScript ya da C++ ve Windows çalışma zamanı tarafından kullanılan WinMD meta verileri içerir.  
  
 Kullanarak derlenmiş bir dosya çıktısını **-target: winmdobj** derleyici seçeneği, yalnızca giriş olarak WimMDExp dışarı aktarma aracı için kullanılmak üzere tasarlanmıştır; .winmdobj dosyasını doğrudan başvuruda değil.  
  
 Kullanmadığınız sürece [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) seçeneği, çıktı dosyası adı ilk giriş dosyasının adını alır. A [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi gerekli değildir.  
  
 Belirtirseniz, target: winmdobj seçeneği bir komut isteminde, sonraki kadar tüm dosyaları **-out** veya [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) seçeneği, Windows programı oluşturmak için kullanılır.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a>Bu derleyici seçeneğini Windows Mağazası uygulaması için Visual Studio IDE'de ayarlamak için  
  
1.  İçinde **Çözüm Gezgini**projeniz için kısayol menüsünü açın ve ardından **özellikleri**.  
  
2.  Seçin **uygulama** sekmesi.  
  
3.  İçinde **çıktı türü** listesinde, seçin **WinMD dosyası**.  
  
     **WinMD dosyası** seçenek, yalnızca kullanılabilir [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] uygulama şablonları.  
  
 Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut derlerken `filename.cs` bir ara .winmdobj dosyasına.  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [-target (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)
