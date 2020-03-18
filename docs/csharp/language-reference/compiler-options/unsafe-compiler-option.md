---
title: -güvenli değil (C# Derleyici Seçenekleri)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 146299fda103567b111c66400c17edf36addd843
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "65877989"
---
# <a name="-unsafe-c-compiler-options"></a>-güvenli değil (C# Derleyici Seçenekleri)

**-güvenli olmayan** derleyici seçeneği derlemek için [güvenli olmayan](../keywords/unsafe.md) anahtar kelime kullanan kod sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a>Açıklamalar

Güvenli olmayan kod hakkında daha fazla bilgi için [Güvenli Olmayan Kod ve İşaretçiler'e](../../programming-guide/unsafe-code-pointers/index.md)bakın.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikleri** sayfasını açın.  
  
2. Özellik **Oluştur** sayfasını tıklatın.  
  
3. Güvenli **Olmayan Koda İzin Ver** onay kutusunu seçin.  
  
### <a name="to-add-this-option-in-a-csproj-file"></a>Bu seçeneği bir csproj dosyasına eklemek için

Bir proje için .csproj dosyasını açın ve aşağıdaki öğeleri ekleyin:

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabilen ler hakkında bilgi için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>  
  
## <a name="example"></a>Örnek

Güvenli `in.cs` olmayan mod için derleme:  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
