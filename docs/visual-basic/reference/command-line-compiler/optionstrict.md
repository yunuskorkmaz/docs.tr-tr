---
title: /optionstrict
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f783cc5b20c4fe6d7812a05a66cbc4cdfc0b9395
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="optionstrict"></a>/optionstrict
Örtük tür dönüşümleri kısıtlamak için kesin türü anlamları zorlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/optionstrict[+ | -]  
/optionstrict[:custom]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 İsteğe bağlı. `/optionstrict+` Seçeneği örtük tür dönüştürmesi kısıtlar. Bu seçenek için varsayılan değer `/optionstrict-`. `/optionstrict+` Seçenektir aynı `/optionstrict`. Her iki izin türü anlamları için kullanabilirsiniz.  
  
 `custom`  
 Gerekli. Kesin dil semantiği değil dikkate olduğunda uyar.  
  
## <a name="remarks"></a>Açıklamalar  
 Zaman `/optionstrict+` , yalnızca genişletme tür dönüştürmeleri örtük olarak sunulabilir etkindir. Örtük daraltma türü dönüşümleri, atama gibi bir `Decimal` türü tamsayı türü nesnesini, hata olarak bildirilir.  
  
 Örtük daraltma tür dönüştürmeleri için uyarıları oluşturmak için kullanmak `/optionstrict:custom`. Kullanım `/nowarn:numberlist` belirli uyarılarını gözardı etme ve `/warnaserror:numberlist` belirli uyarıları hata olarak değerlendirmek için.  
  
### <a name="to-set-optionstrict-in-the-visual-studio-ide"></a>/ Optionstrict Visual Studio IDE'de ayarlamak için  
  
1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri.** Daha fazla bilgi için bkz: [Proje Tasarımcısı giriş](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Tıklatın **derleme** sekmesi.  
  
3.  Değer değiştirme **Option Strict** kutusu.  
  
### <a name="to-set-optionstrict-programmatically"></a>/ Optionstrict programlı olarak ayarlamak için  
  
-   Bkz: [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `Test.vb` kullanarak strict türü anlamları.  
  
```  
vbc /optionstrict+ test.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [/ optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [/ optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [/ nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)  
 [/ warnaserror (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md)  
 [Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Visual Basic Varsayılanları, projeler, Seçenekler iletişim kutusu](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
