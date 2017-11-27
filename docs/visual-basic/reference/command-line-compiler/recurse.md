---
title: /recurse
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb69c7c44dcc2e8da5eb8a76f7d22f936a6d948f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="recurse"></a>/recurse
Belirtilen dizin veya proje dizininin tüm alt dizinlerdeki kaynak kodu dosyaları derler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  
 `dir`  
 İsteğe bağlı. Aramayı başlatmak istediğiniz dizin. Belirtilmezse, arama proje dizininde başlar.  
  
 `file`  
 Gerekli. Aranacak dosya. Joker karakterlere izin verilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Proje dizininde eşleşen tüm dosyaları kullanmadan derlemek için dosya adında joker karakterleri kullanabilirsiniz `/recurse`. Derleyici hiçbir çıktı dosyası adı belirtilirse, işlenen ilk giriş dosyası çıktı dosyası adını temel alır. Bu genellikle ilk alfabetik olarak görüntülendiğinde derlenmiş dosyalar listesinden dosyasıdır. Bu nedenle, bir çıktı dosyası kullanarak belirtmek en iyisidir `/out` seçeneği.  
  
> [!NOTE]
>  `/recurse` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod tüm derler [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] geçerli dizindeki dosyaları.  
  
```  
vbc *.vb  
```  
  
 Aşağıdaki kod tüm derler [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dosyalar `Test\ABC` dizin ve herhangi bir dizinlerinde ve ardından oluşturur `Test.ABC.dll`.  
  
```  
vbc /target:library /out:Test.ABC.dll /recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)  
 [Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
