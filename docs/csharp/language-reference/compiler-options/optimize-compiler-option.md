---
title: "-optimize (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d74a338336d5878cb8d6f212076bb9f1eb7ef768
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="optimize-c-compiler-options"></a>/optimize (C# Derleyici Seçenekleri)
**/ Optimize** seçeneğini etkinleştirir veya çıkış dosyanızın daha küçük, daha hızlı ve daha verimli olmak için derleyici tarafından gerçekleştirilen iyileştirmeleri devre dışı bırakır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
/optimize[+ | -]  
```  
  
## <a name="remarks"></a>Açıklamalar  
 **/ optimize** ayrıca çalışma zamanında kod iyileştirmek için ortak dil çalışma zamanı anlatır.  
  
 Varsayılan olarak, en iyi duruma getirme devre dışıdır. Belirtin **/ optimize +** en iyi duruma getirme etkinleştirmek için.  
  
 Bir derlemesi tarafından kullanılacak bir modül oluştururken, aynı kullanmanız **/ optimize** olanlar derlemenin olarak ayarlar.  
  
 **/o** kısa biçimi olan **/ optimize**.  
  
 Birleştirmek olasıdır **/ optimize** ve [/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) seçenekleri.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açmak **özellikleri** sayfası.  
  
2.  Tıklatın **yapı** özellik sayfası.  
  
3.  Değiştirme **kodu İyileştir** özelliği.  
  
 Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.  
  
## <a name="example"></a>Örnek  
 Derleme `t2.cs` ve derleyici iyileştirmelerini etkinleştirme:  
  
```console  
csc t2.cs /optimize  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)
