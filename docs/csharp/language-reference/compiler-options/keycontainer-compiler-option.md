---
description: -keycontainer (C# derleyici seçenekleri)
title: -keycontainer (C# derleyici seçenekleri)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: 93ee5cd755a4fd6918d2a5825b63151a201a8f6a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91152474"
---
# <a name="-keycontainer-c-compiler-options"></a>-keycontainer (C# derleyici seçenekleri)

Şifreleme anahtarı kapsayıcısının adını belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `string`  
 Tanımlayıcı ad anahtar kapsayıcısının adı.  
  
## <a name="remarks"></a>Açıklamalar  

 **-Keycontainer** seçeneği kullanıldığında, derleyici paylaşılabilir bir bileşen oluşturur. Derleyici, belirtilen kapsayıcıdan derleme bildirimine ortak bir anahtar ekler ve son derlemeyi özel anahtarla imzalar. Anahtar dosyası oluşturmak için `sn -k file` komut satırına yazın. `sn -i` anahtar çiftini bir kapsayıcıya kurar. Derleyici CoreCLR üzerinde çalıştırıldığında bu seçenek desteklenmez. CoreCLR üzerinde oluşturma sırasında bir derlemeyi imzalamak için [-keyfile](keyfile-compiler-option.md) seçeneğini kullanın.
  
 [-Target: Module](./target-module-compiler-option.md)ile derleme yaparsanız, anahtar dosyasının adı modülde tutulur ve bu modülü [-addmodule](./addmodule-compiler-option.md)ile bir derlemede derlerken derlemeye dahil edilir.  
  
 Bu seçeneği, <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType> herhangi bir Microsoft ara dili (MSIL) modülünün kaynak kodunda özel bir öznitelik () olarak da belirtebilirsiniz.  
  
 Ayrıca, [-keyfile](./keyfile-compiler-option.md)ile şifreleme bilgilerinizi derleyiciye geçirebilirsiniz. Ortak anahtarın derleme bildirimine eklenmesini istiyorsanız, ancak test edilene kadar derlemeyi imzalamak istiyorsanız [-delaysign](./delaysign-compiler-option.md) kullanın.  
  
 Daha fazla bilgi için bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](../../../standard/assembly/create-use-strong-named.md) ve [bir derlemeyi imzalamayı geciktirme](../../../standard/assembly/delay-sign.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Bu derleyici seçeneği, Visual Studio geliştirme ortamında kullanılamaz.  
  
 Bu derleyici seçeneğine aracılığıyla programlı bir şekilde erişebilirsiniz <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici-anahtar seçeneği](keyfile-compiler-option.md)
- [C# derleyici seçenekleri](index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
