---
title: -hedef:winmdobj (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: 85ae9a3f5e9b038c0c56935ec5af2b9b09d19f20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204485"
---
# <a name="-targetwinmdobj-c-compiler-options"></a>-hedef:winmdobj (C# Derleyici Seçenekleri)
**-hedef:winmdobj** derleyici sebunu kullanırsanız, derleyici Windows Runtime ikili (.winmd) dosyasına dönüştürebileceğiniz bir ara .winmdobj dosyası oluşturur. .winmd dosyası daha sonra yönetilen dil programlarına ek olarak JavaScript ve C++ programları tarafından da tüketilebilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a>Açıklamalar  
 **Winmdobj** ayarı derleyiciye bir ara modülün gerekli olduğunu bildirir. Buna karşılık, Visual Studio C# sınıf kitaplığını .winmdobj dosyası olarak derler. .winmdobj dosyası daha sonra bir <xref:Microsoft.Build.Tasks.WinMDExp> Windows meta data (.winmd) dosyası oluşturmak için dışa aktarma aracı üzerinden beslenebilir. .winmd dosyası hem özgün kitaplıktaki kodu hem de JavaScript veya C++ ve Windows Runtime tarafından kullanılan WinMD meta verilerini içerir.  
  
 **-target:winmdobj** derleyici seçeneği kullanılarak derlenen bir dosyanın çıktısı yalnızca WimMDExp dışa aktarma aracı nın girişi olarak kullanılmak üzere tasarlanmıştır; .winmdobj dosyasının kendisi doğrudan başvurulmuyor.  
  
 [-out](./out-compiler-option.md) seçeneğini kullanmadığınız sürece, çıktı dosyası adı ilk giriş dosyasının adını alır. [Ana](../../programming-guide/main-and-command-args/index.md) yöntem gerekli değildir.  
  
 Komut isteminde -hedef:winmdobj seçeneğini belirtirseniz, Windows programını oluşturmak için bir sonraki **-out** veya [-target:module](./target-module-compiler-option.md) seçeneğine kadar tüm dosyalar kullanılır.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a>Bu derleyici seçeneğini Windows Mağazası uygulaması için Visual Studio IDE'de ayarlamak için  
  
1. **Çözüm Gezgini'nde,** projenizin kısayol menüsünü açın ve ardından **Özellikler'i**seçin.  
  
2. **Uygulama** sekmesini seçin.  
  
3. Çıktı **türü** listesinde **WinMD Dosyası'nı**seçin.  
  
     **WinMD Dosyası** seçeneği yalnızca Windows 8.x Store uygulama şablonları için kullanılabilir.  
  
 Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabilen ler hakkında bilgi için bkz. <xref:VSLangProj80.ProjectProperties3.OutputType%2A>  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut bir `filename.cs` ara .winmdobj dosyasında derler.  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-hedef (C# Derleyici Seçenekleri)](./target-compiler-option.md)
- [C# Derleyici Seçenekleri](./index.md)
