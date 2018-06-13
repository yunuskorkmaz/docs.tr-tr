---
title: -optimize (C# Derleyici Seçenekleri)
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
ms.openlocfilehash: 86c8ebb2d2061085be4c00e8ac95448e1c341161
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33212468"
---
# <a name="-optimize-c-compiler-options"></a>-optimize (C# Derleyici Seçenekleri)
**-En iyi duruma getirme** seçeneğini etkinleştirir veya çıkış dosyanızın daha küçük, daha hızlı ve daha verimli olmak için derleyici tarafından gerçekleştirilen iyileştirmeleri devre dışı bırakır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 **-en iyi duruma getirme** ayrıca çalışma zamanında kod iyileştirmek için ortak dil çalışma zamanı anlatır.  
  
 Varsayılan olarak, en iyi duruma getirme devre dışıdır. Belirtin **-en iyi duruma getirme +** en iyi duruma getirme etkinleştirmek için.  
  
 Bir derlemesi tarafından kullanılacak bir modül oluştururken, aynı kullanmanız **-en iyi duruma getirme** olanlar derlemenin olarak ayarlar.  
  
 **-o** kısa biçimi olan **-en iyi duruma getirme**.  
  
 Birleştirmek olasıdır **-en iyi duruma getirme** ve [-debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) seçenekleri.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açmak **özellikleri** sayfası.  
  
2.  Tıklatın **yapı** özellik sayfası.  
  
3.  Değiştirme **kodu İyileştir** özelliği.  
  
 Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.  
  
## <a name="example"></a>Örnek  
 Derleme `t2.cs` ve derleyici iyileştirmelerini etkinleştirme:  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
