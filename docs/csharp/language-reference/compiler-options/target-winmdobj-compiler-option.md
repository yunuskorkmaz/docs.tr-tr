---
title: '-target: winmdobj (C# derleyici seçenekleri)'
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: 85ae9a3f5e9b038c0c56935ec5af2b9b09d19f20
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204485"
---
# <a name="-targetwinmdobj-c-compiler-options"></a>-target: winmdobj (C# derleyici seçenekleri)
**-Target: winmdobj** derleyici seçeneğini kullanırsanız, derleyici Windows çalışma zamanı ikili (. winmd) dosyasına dönüştürebileceğiniz bir ara. winmdobj dosyası oluşturur. . Winmd dosyası daha sonra JavaScript ve C++ programlar tarafından, yönetilen dil programlarına ek olarak tüketilebilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a>Açıklamalar  
 **Winmdobj** ayarı derleyiciye bir ara modülün gerekli olduğunu bildirir. Yanıt olarak, Visual Studio C# sınıf kitaplığını bir. winmdobj dosyası olarak derler. . Winmdobj dosyası daha sonra bir Windows meta veri (. winmd) dosyası oluşturmak için <xref:Microsoft.Build.Tasks.WinMDExp> dışarı aktarma aracı aracılığıyla beslenebilir. . Winmd dosyası, özgün kitaplıktan kodu ve JavaScript veya C++ Windows çalışma zamanı tarafından kullanılan winmd meta verilerini içerir.  
  
 **-Target: winmdobj** derleyici seçeneği kullanılarak derlenen bir dosyanın çıktısı yalnızca Wımmdexp Export aracı için giriş olarak kullanılmak üzere tasarlanmıştır; . winmdobj dosyasının kendisine doğrudan başvurulmuyor.  
  
 [-Out](./out-compiler-option.md) seçeneğini kullanmadığınız takdirde, çıkış dosyası adı ilk giriş dosyasının adını alır. [Main](../../programming-guide/main-and-command-args/index.md) yöntemi gerekli değildir.  
  
 Bir komut isteminde-target: winmdobj seçeneğini belirtirseniz, Windows programını oluşturmak için bir sonraki **-Out** veya [-target: Module](./target-module-compiler-option.md) seçeneği görüntüleninceye kadar tüm dosyalar kullanılır.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a>Bu derleyici seçeneğini Windows Mağazası uygulaması için Visual Studio IDE'de ayarlamak için  
  
1. **Çözüm Gezgini**' de, projeniz için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.  
  
2. **Uygulama** sekmesini seçin.  
  
3. **Çıktı türü** listesinde, **winmd dosyası**' nı seçin.  
  
     **Winmd dosyası** seçeneği yalnızca Windows 8. x Mağazası uygulama şablonları için kullanılabilir.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut `filename.cs` bir ara. winmdobj dosyasına derler.  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-target (C# derleyici seçenekleri)](./target-compiler-option.md)
- [C# Derleyici Seçenekleri](./index.md)
