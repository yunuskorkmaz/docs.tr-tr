---
title: -recurse
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb1cc114c2882aa82787f94a271dd7684c716b01
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-recurse"></a>-recurse
Belirtilen dizin veya proje dizininin tüm alt dizinlerdeki kaynak kodu dosyaları derler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  
 `dir`  
 İsteğe bağlı. Aramayı başlatmak istediğiniz dizin. Belirtilmezse, arama proje dizininde başlar.  
  
 `file`  
 Gerekli. Aranacak dosya. Joker karakterlere izin verilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Proje dizininde eşleşen tüm dosyaları kullanmadan derlemek için dosya adında joker karakterleri kullanabilirsiniz `-recurse`. Derleyici hiçbir çıktı dosyası adı belirtilirse, işlenen ilk giriş dosyası çıktı dosyası adını temel alır. Bu genellikle ilk alfabetik olarak görüntülendiğinde derlenmiş dosyalar listesinden dosyasıdır. Bu nedenle, bir çıktı dosyası kullanarak belirtmek en iyisidir `-out` seçeneği.  
  
> [!NOTE]
>  `-recurse` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komutu tüm derler [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] geçerli dizindeki dosyaları.  
  
```console
vbc *.vb  
```  
  
 Aşağıdaki komutu tüm derler [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dosyalar `Test\ABC` dizin ve herhangi bir dizinlerinde ve ardından oluşturur `Test.ABC.dll`.  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
