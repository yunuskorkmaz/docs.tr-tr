---
title: -unsafe (C# Derleyici Seçenekleri)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 4cfd7c82bc2cbf816164b235642c0647eeb7e5b6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337337"
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
  
1. Projenin açın **özellikleri** sayfası.  
  
2. Tıklayın **derleme** özellik sayfası.  
  
3. Seçin **güvenli olmayan koda izin ver** onay kutusu.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
