---
title: -keycontainer (C# derleyici seçenekleri)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: 0d4ca602859c4f7f80a8fcdc09182c7da8a5fb31
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602843"
---
# <a name="-keycontainer-c-compiler-options"></a>-keycontainer (C# derleyici seçenekleri)
Şifreleme anahtarı kapsayıcısının adını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a>Arguments  
 `string`  
 Tanımlayıcı ad anahtar kapsayıcısının adı.  
  
## <a name="remarks"></a>Açıklamalar  
 **-Keycontainer** seçeneği kullanıldığında, derleyici paylaşılabilir bir bileşen oluşturur. Derleyici, belirtilen kapsayıcıdan derleme bildirimine ortak bir anahtar ekler ve son derlemeyi özel anahtarla imzalar. Anahtar dosyası oluşturmak için komut satırına yazın `sn -k file` . `sn -i`anahtar çiftini bir kapsayıcıya kurar. Derleyici CoreCLR üzerinde çalıştırıldığında bu seçenek desteklenmez. CoreCLR üzerinde oluşturma sırasında bir derlemeyi imzalamak için [-keyfile](keyfile-compiler-option.md) seçeneğini kullanın.
  
 [-Target: Module](./target-module-compiler-option.md)ile derleme yaparsanız, anahtar dosyasının adı modülde tutulur ve bu modülü [-addmodule](./addmodule-compiler-option.md)ile bir derlemede derlerken derlemeye dahil edilir.  
  
 Bu seçeneği, herhangi bir Microsoft ara dili (MSIL)<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>modülünün kaynak kodunda özel bir öznitelik () olarak da belirtebilirsiniz.  
  
 Ayrıca, [-keyfile](./keyfile-compiler-option.md)ile şifreleme bilgilerinizi derleyiciye geçirebilirsiniz. Ortak anahtarın derleme bildirimine eklenmesini istiyorsanız, ancak test edilene kadar derlemeyi imzalamak istiyorsanız [-delaysign](./delaysign-compiler-option.md) kullanın.  
  
 Daha fazla bilgi için bkz. [güçlü adlandırılmış derlemeler oluşturma ve kullanma](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) ve [bir derlemeyi imzalamayı geciktirme](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Bu derleyici seçeneği, Visual Studio geliştirme ortamında kullanılamaz.  
  
 Bu derleyici seçeneğine <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>aracılığıyla programlı bir şekilde erişebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Derleyici-anahtar seçeneği](keyfile-compiler-option.md)
- [C# Derleyici Seçenekleri](index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
