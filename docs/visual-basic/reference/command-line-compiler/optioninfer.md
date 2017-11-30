---
title: /optioninfer
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4400ee58214c8f9990d4b123e17ef0f6553a5a69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="optioninfer"></a>/optioninfer
Yerel türü çıkarımı değişken bildirimlerden kullanımını etkinleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/optioninfer[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`+` &#124; `-`|İsteğe bağlı. Belirtin `/optioninfer+` yerel türü çıkarımı etkinleştirmek için veya `/optioninfer-` bunu engellemek için. `/optioninfer` Seçeneği, belirtilen herhangi bir değer ile aynı olup `/optioninfer+`. Varsayılan değer `/optioninfer` anahtar mevcut değil de `/optioninfer+`. Varsayılan değer Vbc.rsp yanıt dosyasında ayarlanır.|  
  
> [!NOTE]
>  Kullanabileceğiniz `/noconfig` seçeneği vbc.rsp içinde belirtilen yerine derleyicinin iç Varsayılanları koruyun. Bu seçenek için derleyici varsayılan değer `/optioninfer-`.  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynak kodu dosyasının içeriyorsa bir [Option Infer deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md), deyim için geçersiz kılar `/optioninfer` komut satırı derleyicisi ayarı.  
  
### <a name="to-set-optioninfer-in-the-visual-studio-ide"></a>/ Optioninfer Visual Studio IDE'de ayarlamak için  
  
1.  Bir projedeki seçin **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**. Daha fazla bilgi için bkz: [NIB: Proje özellikleriyle yönetme Proje Tasarımcısı](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).  
  
2.  Üzerinde **derleme** sekmesinde, değeri Değiştir **Option Infer** kutusu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `test.vb` etkin yerel türü çıkarımı ile.  
  
```  
vbc /optioninfer+ test.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [/ optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [/ optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Option Infer deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Visual Basic Varsayılanları, projeler, Seçenekler iletişim kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [Derle sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [/ noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [Komut satırından oluşturma](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
