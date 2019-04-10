---
title: -keycontaıner (C# Derleyici Seçenekleri)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: cf51bccc98f04c38149ec821b7064a4844d7e804
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302783"
---
# <a name="-keycontainer-c-compiler-options"></a>-keycontaıner (C# Derleyici Seçenekleri)
Şifreleme anahtar kapsayıcısı adını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a>Arguments  
 `string`  
 Tanımlayıcı ad anahtar kapsayıcısı adı.  
  
## <a name="remarks"></a>Açıklamalar  
 Zaman **- keycontaıner** seçeneği kullanıldığında, derleyici paylaşılabilir bir bileşen oluşturur. Derleyici, bir ortak anahtar belirtilen kapsayıcısından derleme bildirimine ekler ve son derlemeyi özel anahtarla imzalar. Bir anahtar dosyası oluşturmak için şunu yazın `sn -k file` komut satırına. `sn -i` bir kapsayıcıya anahtar çifti yükler. CoreCLR derleyici çalıştığında, bu seçeneği desteklenmiyor. Coreclr'de derlerken bir derlemeyi imzalamak için kullanmak [- keyfile](keyfile-compiler-option.md) seçeneği.
  
 Derleme yaparsanız [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), anahtar dosyasının adını modülde tutulur ve sahip bir derleme içine bu modülü derlerken bütünleştirilmiş kod içine dahil [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Bu seçenek özel bir öznitelik belirtebilirsiniz (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) herhangi bir Microsoft Ara dili (MSIL) modülü için kaynak kodunda.  
  
 Derleyici ile şifreleme bilgilerinizi de geçirebilirsiniz [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md). Kullanım [- delaysıgn](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) ortak anahtarı derleme bildirimine eklenmesini istediğiniz ancak edilmiş olan kadar derlemeyi imzalamayı geciktirme istiyorsunuz.  
  
 Daha fazla bilgi için [bkz](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) ve [derlemeyi imzalamayı geciktirme](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Bu derleyici seçeneğini Visual Studio geliştirme ortamında kullanılabilir değil.  
  
 Bu derleyici seçeneği ile program aracılığıyla erişebileceğiniz <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyicisi - keyfıle seçeneği](keyfile-compiler-option.md)
- [C# Derleyici Seçenekleri](index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
