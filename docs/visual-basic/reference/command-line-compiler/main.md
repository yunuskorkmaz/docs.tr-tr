---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: 91f2a27ed9b6fb296dbb9e50fc488fd012311890
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005498"
---
# <a name="-main"></a>-main
@No__t-0 yordamını içeren sınıfı veya modülü belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-main:location  
```  
  
## <a name="arguments"></a>Arguments  
 `location`  
 Gerekli. Program başladığında çağrılacak `Sub Main` yordamını içeren sınıfın veya modülün adı. Bu, **-Main: Module** veya **-Main: Namespace. Module**biçiminde olabilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Yürütülebilir bir dosya veya Windows yürütülebilir programı oluştururken bu seçeneği kullanın. **-Main** seçeneği atlanırsa, derleyici tüm ortak sınıflarda ve modüllerde geçerli bir paylaşılan `Sub Main` arar.  
  
 @No__t-1 yordamının çeşitli biçimlerinin tartışılması için [Visual Basic 'de ana yordama](../../../visual-basic/programming-guide/program-structure/main-procedure.md) bakın.  
  
 @No__t-0 <xref:System.Windows.Forms.Form> ' den devralan bir sınıfsa, derleyici, bir @no__t 3 yordamı yoksa uygulamayı başlatan varsayılan bir `Main` yordamı sağlar. Bu, geliştirme ortamında oluşturulan komut satırında kod derlemenize olanak sağlar.  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a>Visual Studio tümleşik geliştirme ortamında Main 'i ayarlamak için  
  
1. **Çözüm Gezgini**' de bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Uygulama** sekmesine tıklayın.  
  
3. **Uygulama çerçevesini etkinleştir** onay kutusunun işaretli olmadığından emin olun.  
  
4. **Başlangıç nesnesi** kutusundaki değeri değiştirin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, `Test2` sınıfında `Sub Main` yordamının bulunduğunu belirten `T2.vb` ve `T3.vb` ' i derler.  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Visual Basic ana yordam](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
