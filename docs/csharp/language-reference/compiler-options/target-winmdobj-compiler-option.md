---
title: '-target: winmdobj (C# derleyici seçenekleri)'
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: fe1332f9ed6de9c50c2509e29f22ed7c0e57ade9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606350"
---
# <a name="-targetwinmdobj-c-compiler-options"></a>-target: winmdobj (C# derleyici seçenekleri)
**-Target: winmdobj** derleyici seçeneğini kullanırsanız, derleyici Windows çalışma zamanı ikili (. winmd) dosyasına dönüştürebileceğiniz bir ara. winmdobj dosyası oluşturur. . Winmd dosyası daha sonra JavaScript ve C++ programlar tarafından, yönetilen dil programlarına ek olarak tüketilebilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a>Açıklamalar  
 **Winmdobj** ayarı derleyiciye bir ara modülün gerekli olduğunu bildirir. Yanıt olarak, Visual Studio C# sınıf kitaplığını bir. winmdobj dosyası olarak derler. . Winmdobj dosyası daha sonra bir Windows meta veri ( <xref:Microsoft.Build.Tasks.WinMDExp> . winmd) dosyası oluşturmak için dışarı aktarma aracından beslenebilir. . Winmd dosyası, özgün kitaplıktan kodu ve JavaScript veya C++ Windows çalışma zamanı tarafından kullanılan winmd meta verilerini içerir.  
  
 **-Target: winmdobj** derleyici seçeneği kullanılarak derlenen bir dosyanın çıktısı yalnızca Wımmdexp Export aracı için giriş olarak kullanılmak üzere tasarlanmıştır; . winmdobj dosyasının kendisine doğrudan başvurulmuyor.  
  
 [-Out](./out-compiler-option.md) seçeneğini kullanmadığınız takdirde, çıkış dosyası adı ilk giriş dosyasının adını alır. [Main](../../programming-guide/main-and-command-args/index.md) yöntemi gerekli değildir.  
  
 Bir komut isteminde-target: winmdobj seçeneğini belirtirseniz, Windows programını oluşturmak için bir sonraki **-Out** veya [-target: Module](./target-module-compiler-option.md) seçeneği görüntüleninceye kadar tüm dosyalar kullanılır.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a>Bu derleyici seçeneğini Windows Mağazası uygulaması için Visual Studio IDE'de ayarlamak için  
  
1. **Çözüm Gezgini**' de, projeniz için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.  
  
2. **Uygulama** sekmesini seçin.  
  
3. **Çıktı türü** listesinde, **winmd dosyası**' nı seçin.  
  
     **Winmd dosyası** seçeneği yalnızca uygulama şablonları için [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] kullanılabilir.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut bir ara `filename.cs` . winmdobj dosyası içinde derlenir.  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-target (C# derleyici seçenekleri)](./target-compiler-option.md)
- [C# Derleyici Seçenekleri](./index.md)
