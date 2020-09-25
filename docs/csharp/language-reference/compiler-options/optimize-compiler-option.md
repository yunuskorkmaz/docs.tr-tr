---
description: -optimize (C# derleyici seçenekleri)
title: -optimize (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
ms.openlocfilehash: 1862794e4d823e38ce19780300a0b04f4e57dc44
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193991"
---
# <a name="-optimize-c-compiler-options"></a>-optimize (C# derleyici seçenekleri)

**-Optimize** seçeneği, çıkış dosyanızı daha küçük, daha hızlı ve daha verimli hale getirmek için derleyici tarafından gerçekleştirilen iyileştirmeleri sağlar veya devre dışı bırakır.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a>Açıklamalar  

 **-optimize** , ortak dil çalışma zamanına kodu çalışma zamanında iyileştirmek için de bildirir.  
  
 Varsayılan olarak, iyileştirmeler devre dışıdır. İyileştirmeleri etkinleştirmek için **-optimize +** belirtin.  
  
 Bir derleme tarafından kullanılacak bir modül oluştururken, derlemeden **en iyileştirme** ayarlarını kullanın.  
  
 **-o** , **en iyileştirme**için kısa bir formdur.  
  
 **-Optimize** ve [-Debug](./debug-compiler-option.md) seçeneklerini birleştirmek mümkündür.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın.  
  
2. **Yapı** özelliği sayfasına tıklayın.  
  
3. **Optimizasyon kodu** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A> ..  
  
## <a name="example"></a>Örnek  

 `t2.cs`Derleyici iyileştirmelerini derleyin ve etkinleştirin:  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
