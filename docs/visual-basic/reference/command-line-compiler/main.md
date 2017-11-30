---
title: /main
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2697b837a536b1b879196bd10843a2b76314747a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="main"></a>/main
Sınıf veya içeren modülünü belirtir `Sub Main` yordamı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/main:location  
```  
  
## <a name="arguments"></a>Arguments  
 `location`  
 Gerekli. Tam nitelenmiş sınıfı ya da içeren modülünü `Sub Main` program başladığında çağrılacak yordamı. Bu formda olabilir **/main:module** veya **/main:namespace.module**.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir yürütülebilir dosya veya Windows yürütülebilir program oluşturduğunuzda, bu seçeneği kullanın. Varsa **/ana** seçeneği atlanırsa, derleyici geçerli bir için paylaşılan arar `Sub Main` tüm ortak sınıfları ve modüller.  
  
 Bkz: [Visual Basic'de ana yordam](../../../visual-basic/programming-guide/program-structure/main-procedure.md) çeşitli formlarının Tartışması için `Main` yordamı.  
  
 Zaman `location` öğesinden devralınan bir sınıf <xref:System.Windows.Forms.Form>, varsayılan derleyici sağlar `Main` sınıfı Hayır ise, uygulama başladığında yordamı `Main` yordamı. Bu, komut satırında geliştirme ortamında oluşturulan kod derleme sağlar.  
  
 [!code-vb[VbVbalrCompiler#16](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]  
  
### <a name="to-set-main-in-the-visual-studio-integrated-development-environment"></a>Tümleşik geliştirme ortamı/Main Visual Studio'da ayarlamak için  
  
1.  Seçili bir projeyi **Çözüm Gezgini**. Üzerinde **proje** menüsünde tıklatın **özellikleri**.  
  
     Daha fazla bilgi için bkz: [Proje Tasarımcısı giriş](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Tıklatın **uygulama** sekmesi.  
  
3.  Emin olun **etkinleştir uygulama çerçevesi** onay kutusu işaretli değildir.  
  
4.  Değer değiştirme **Başlangıç nesnesi** kutusu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlerken `T2.vb` ve `T3.vb`, belirtme, `Sub Main` yordamı bulunan `Test2` sınıfı.  
  
```  
vbc t2.vb t3.vb /main:Test2  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [NIB: Visual Basic Hello, World sürümü](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c)  
 [Visual Basic'de ana yordam](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
