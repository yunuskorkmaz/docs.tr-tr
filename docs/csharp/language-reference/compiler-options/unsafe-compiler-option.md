---
title: -unsafe (C# Derleyici Seçenekleri)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 138c7cce83fd069f44025c57e52b2d01bcb23432
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518056"
---
# <a name="-unsafe-c-compiler-options"></a>-unsafe (C# Derleyici Seçenekleri)
**-Unsafe** derleyici seçeneği verir kullanan kod [güvenli](../../../csharp/language-reference/keywords/unsafe.md) derlemek için anahtar sözcüğü.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Güvenli olmayan kod hakkında daha fazla bilgi için bkz: [güvenli olmayan kod ve işaretçiler](../../../csharp/programming-guide/unsafe-code-pointers/index.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açın **özellikleri** sayfası.  
  
2.  Tıklayın **derleme** özellik sayfası.  
  
3.  Seçin **güvenli olmayan koda izin ver** onay kutusu.  
  
### <a name="to-add-this-option-in-a-csproj-file"></a>Bu seçenek csproj dosyasında eklemek için

Projesi için .csproj dosyasını açın ve aşağıdaki öğeleri ekleyin:

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 Bu derleyici seçeneğini program üzerinden ayarlamak hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.  
  
## <a name="example"></a>Örnek  
 Derleme `in.cs` güvenli olmayan modu:  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
