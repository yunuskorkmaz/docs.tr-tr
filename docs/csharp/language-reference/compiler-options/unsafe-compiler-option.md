---
description: -unsafe (C# derleyici seçenekleri)
title: -unsafe (C# derleyici seçenekleri)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 0f6d94dd25a020d96430746c4b5e7aefd0f679da
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89140847"
---
# <a name="-unsafe-c-compiler-options"></a>-unsafe (C# derleyici seçenekleri)

**-Unsafe** derleyici seçeneği, [unsafe](../keywords/unsafe.md) anahtar sözcüğünü kullanan koda derleme için izin verir.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a>Açıklamalar

Güvenli olmayan kod hakkında daha fazla bilgi için bkz. [güvenli olmayan kod ve işaretçiler](../../programming-guide/unsafe-code-pointers/index.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın.  
  
2. **Yapı** özelliği sayfasına tıklayın.  
  
3. **Güvenli olmayan koda Izin ver** onay kutusunu seçin.  
  
### <a name="to-add-this-option-in-a-csproj-file"></a>Bu seçeneği bir csproj dosyasına eklemek için

Bir proje için. csproj dosyasını açın ve aşağıdaki öğeleri ekleyin:

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A> ..  
  
## <a name="example"></a>Örnek

`in.cs`Güvenli olmayan mod için derle:  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
