---
title: -keycontainer (C# Derleyici Seçenekleri)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: fead2d4296cfa6fb0195cb4b43f6448c0fc7e6a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970145"
---
# <a name="-keycontainer-c-compiler-options"></a>-keycontainer (C# Derleyici Seçenekleri)
Şifreleme anahtar kapsayıcısının adını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `string`  
 Güçlü ad anahtar kapsayıcısının adı.  
  
## <a name="remarks"></a>Açıklamalar  
 **-keycontainer** seçeneği kullanıldığında, derleyici sharable bir bileşen oluşturur. Derleyici, belirtilen kapsayıcıdan ortak bir anahtarı montaj bildirimine ekler ve son derlemeyi özel anahtarla imzalar. Anahtar dosyası oluşturmak için `sn -k file` komut satırına yazın. `sn -i`anahtar çiftini bir kapsayıcıya yükler. Derleyici CoreCLR'de çalıştığında bu seçenek desteklenmez. CoreCLR'da montaj yaparken bir derlemeyi imzalamak için [-keyfile](keyfile-compiler-option.md) seçeneğini kullanın.
  
 [-target:module](./target-module-compiler-option.md)ile derlerseniz, anahtar dosyasının adı modülde tutulur ve bu modülü [-addmodule](./addmodule-compiler-option.md)ile bir derlemeye eklediğinizde derlemeye dahil edilir.  
  
 Bu seçeneği, herhangi bir Microsoft ara<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>dili (MSIL) modülü için kaynak kodunda özel bir öznitelik ( ) olarak da belirtebilirsiniz.  
  
 Şifreleme bilgilerinizi [-keyfile](./keyfile-compiler-option.md)ile derleyiciye de iletebilirsiniz. Ortak anahtarın derleme bildirimine eklenmesini istiyorsanız, ancak derlemenin test edilene kadar imzalanmasını geciktirmek istiyorsanız [-geciktirme işaretini](./delaysign-compiler-option.md) kullanın.  
  
 Daha fazla bilgi için [bkz.](../../../standard/assembly/create-use-strong-named.md) [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Bu derleyici seçeneği Visual Studio geliştirme ortamında kullanılamaz.  
  
 Bu derleyici seçeneğine programlı <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>olarak erişebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici -keyfile seçeneği](keyfile-compiler-option.md)
- [C# Derleyici Seçenekleri](index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
