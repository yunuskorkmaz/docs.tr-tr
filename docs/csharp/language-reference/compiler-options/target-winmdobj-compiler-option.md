---
description: '-target: winmdobj (C# derleyici seçenekleri)'
title: '-target: winmdobj (C# derleyici seçenekleri)'
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: a13e2da02698209a514e716d65c1df3508cf1508
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171409"
---
# <a name="-targetwinmdobj-c-compiler-options"></a>-target: winmdobj (C# derleyici seçenekleri)

**-Target: winmdobj** derleyici seçeneğini kullanırsanız, derleyici Windows çalışma zamanı ikili (. winmd) dosyasına dönüştürebileceğiniz bir ara. winmdobj dosyası oluşturur. . Winmd dosyası daha sonra JavaScript ve C++ programları tarafından, yönetilen dil programlarına ek olarak tüketilebilir.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a>Açıklamalar  

 **Winmdobj** ayarı derleyiciye bir ara modülün gerekli olduğunu bildirir. Yanıt olarak, Visual Studio C# sınıf kitaplığını bir. winmdobj dosyası olarak derler. . Winmdobj dosyası daha sonra <xref:Microsoft.Build.Tasks.WinMDExp> bir Windows meta veri (. winmd) dosyası oluşturmak için dışarı aktarma aracından beslenebilir. . Winmd dosyası, özgün kitaplıktan kodu ve JavaScript ya da C++ tarafından kullanılan WinMD meta verilerini ve Windows Çalışma Zamanı içerir.  
  
 **-Target: winmdobj** derleyici seçeneği kullanılarak derlenen bir dosyanın çıktısı yalnızca Wımmdexp Export aracı için giriş olarak kullanılmak üzere tasarlanmıştır; . winmdobj dosyasının kendisine doğrudan başvurulmuyor.  
  
 [-Out](./out-compiler-option.md) seçeneğini kullanmadığınız takdirde, çıkış dosyası adı ilk giriş dosyasının adını alır. [Main](../../programming-guide/main-and-command-args/index.md) yöntemi gerekli değildir.  
  
 Bir komut isteminde-target: winmdobj seçeneğini belirtirseniz, Windows programını oluşturmak için bir sonraki **-Out** veya [-target: Module](./target-module-compiler-option.md) seçeneği görüntüleninceye kadar tüm dosyalar kullanılır.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a>Bu derleyici seçeneğini Windows Mağazası uygulaması için Visual Studio IDE'de ayarlamak için  
  
1. **Çözüm Gezgini**' de, projeniz için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.  
  
2. **Uygulama** sekmesini seçin.  
  
3. **Çıktı türü** listesinde, **winmd dosyası**' nı seçin.  
  
     **Winmd dosyası** seçeneği yalnızca Windows 8. x Mağazası uygulama şablonları için kullanılabilir.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.OutputType%2A> ..  
  
## <a name="example"></a>Örnek  

 Aşağıdaki komut `filename.cs` bir ara. winmdobj dosyası içinde derlenir.  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-target (C# derleyici seçenekleri)](./target-compiler-option.md)
- [C# derleyici seçenekleri](./index.md)
