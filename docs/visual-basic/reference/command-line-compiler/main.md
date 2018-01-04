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
ms.openlocfilehash: c5bb11bc62e951339113f4b48e98e05362490ca1
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
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
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Visual Basic'de ana yordam](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
