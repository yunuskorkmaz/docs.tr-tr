---
title: -keycontainer (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: edb50dafa376abe55fbeeb312ca5bb8f34c83e7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="-keycontainer-c-compiler-options"></a>-keycontainer (C# Derleyici Seçenekleri)
Şifreleme anahtarı kapsayıcısının adını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a>Arguments  
 `string`  
 Güçlü ad anahtar kapsayıcısı adı.  
  
## <a name="remarks"></a>Açıklamalar  
 Zaman **- keycontainer** seçeneği kullanıldığında, bir ortak anahtar belirtilmiş kapsayıcıdan derleme bildirimine ekleme ve özel anahtarla son derleme imzalama tarafından paylaşılabilir bir bileşen derleyici oluşturur. Bir anahtar dosyası oluşturmak için sn -k yazın `file` komut satırında. sn -i anahtar çiftini bir kapsayıcıya yükler.  
  
 İle derleme yaparsanız [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), anahtar dosyasının adı modülde tutulur ve bir derleme halinde bu modül derlediğinizde derlemeye birleştirilmiş [- addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Bu seçenek özel bir öznitelik belirtebilirsiniz (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) herhangi bir Microsoft Ara dili (MSIL) modülü için kaynak kodundaki.  
  
 Derleyici ile şifreleme bilgilerinizi geçirebilirsiniz [- keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md). Kullanım [- delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) ortak anahtar derleme bildirimi eklenmesini istediğiniz ancak test edilmiştir kadar derleme imzalamayı geciktirme istersiniz.  
  
 Daha fazla bilgi için bkz: [bkz](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) ve [Gecikmeli bir derleme imzalama](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Bu derleyici seçeneği Visual Studio geliştirme ortamında kullanılabilir değil.  
  
 Bu derleyici seçeneği ile program aracılığıyla erişebilirsiniz <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
