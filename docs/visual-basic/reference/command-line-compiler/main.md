---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: fd6240faf702ccb5e543bfd6a7779284f38d8850
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337246"
---
# <a name="-main"></a>-main
Sınıf veya içeren modül belirtir `Sub Main` yordamı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-main:location  
```  
  
## <a name="arguments"></a>Arguments  
 `location`  
 Gerekli. Sınıf veya içeren modül adını `Sub Main` yordamı, program başladığında çağrılabilir. Bu biçiminde olabilir **-main: Modül** veya **-main:namespace.module**.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir yürütülebilir dosya ya da Windows yürütülebilir program oluşturduğunuzda bu seçeneği kullanın. Varsa **-ana** seçeneği atlanırsa, derleyici için geçerli paylaşılan arar `Sub Main` tüm ortak sınıfları ve modüller.  
  
 Bkz: [Visual Basic'de ana yordam](../../../visual-basic/programming-guide/program-structure/main-procedure.md) çeşitli türleri, bir irdelemesi `Main` yordamı.  
  
 Zaman `location` devralan bir sınıf olan <xref:System.Windows.Forms.Form>, derleyici varsayılan bir ıloggerfactory sağlar `Main` sınıfı Hayır ise, uygulama başladığında yordamı `Main` yordamı. Bu, kodu geliştirme ortamında oluşturulmuş komut satırında derleme sağlar.  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a>-Ana Visual Studio tümleşik geliştirme ortamında ayarlamak için  
  
1. Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünü tıklatın **özellikleri**.  
  
2. Tıklayın **uygulama** sekmesi.  
  
3. Emin **etkinleştir uygulama çerçevesi** onay kutusu işaretli değildir.  
  
4. Değer değiştirme **Başlangıç nesnesi** kutusu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `T2.vb` ve `T3.vb`, belirtilmesi, `Sub Main` yordamı bulunan `Test2` sınıfı.  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Komut Satırı Derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Visual Basic'de Ana Yordam](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
