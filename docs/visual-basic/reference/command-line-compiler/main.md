---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: fb317b3c555d151e132122c476ce19bdeceb1321
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91065625"
---
# <a name="-main"></a>-main

Yordamı içeren sınıfı veya modülü belirtir `Sub Main` .  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-main:location  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `location`  
 Gereklidir. Program başlatıldığında Çağrılacak yordamı içeren sınıfın veya modülün adı `Sub Main` . Bu, **-Main: Module** veya **-Main: Namespace. Module**biçiminde olabilir.  
  
## <a name="remarks"></a>Açıklamalar  

 Yürütülebilir bir dosya veya Windows yürütülebilir programı oluştururken bu seçeneği kullanın. **-Main** seçeneği atlanırsa, derleyici `Sub Main` tüm ortak sınıflarda ve modüllerde geçerli bir paylaşılan arar.  
  
 Yordamın çeşitli biçimlerinin tartışılması için [Visual Basic ana yordama](../../programming-guide/program-structure/main-procedure.md) bakın `Main` .  
  
 Sınıfından `location` devralan bir sınıf olduğunda <xref:System.Windows.Forms.Form> , derleyici bir `Main` yordam yoksa, uygulamayı başlatan varsayılan bir yordam sağlar `Main` . Bu, geliştirme ortamında oluşturulan komut satırında kod derlemenize olanak sağlar.  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a>Visual Studio tümleşik geliştirme ortamında Main 'i ayarlamak için  
  
1. **Çözüm Gezgini**' de bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Uygulama** sekmesine tıklayın.  
  
3. **Uygulama çerçevesini etkinleştir** onay kutusunun işaretli olmadığından emin olun.  
  
4. **Başlangıç nesnesi** kutusundaki değeri değiştirin.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, `T2.vb` ve `T3.vb` yordamının sınıfında bulunduğunu belirtmek için derleme `Sub Main` yapar `Test2` .  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](index.md)
- [-target (Visual Basic)](target.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
- [Visual Basic'de Ana Yordam](../../programming-guide/program-structure/main-procedure.md)
