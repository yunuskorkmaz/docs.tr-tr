---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 2fe1834c3e92c3eff016ffd7857a0473eb2e8b3a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788862"
---
# <a name="-recurse"></a>-recurse
Belirtilen dizin veya proje dizininin tüm alt dizinlerdeki kaynak kodu dosyaları derler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  
 `dir`  
 İsteğe bağlı. Aramayı başlatmak istediğiniz dizin. Belirtilmemişse, arama proje dizininde başlar.  
  
 `file`  
 Gerekli. Aranacak dosya. Joker karakterlere izin verilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Proje dizininde eşleşen tüm dosyaları kullanmadan derlemek için bir dosya adında joker karakterler kullanabilirsiniz `-recurse`. Hiçbir çıkış dosyası adı belirtilirse, derleyicinin işlenen ilk giriş dosyasının çıkış dosya adını alır. Bu genellikle ilk görüntülendiğinde alfabetik olarak derlenmiş dosyalar listesinden dosyasıdır. Bu nedenle, bir çıkış dosyası kullanarak belirtmek en iyi `-out` seçeneği.  
  
> [!NOTE]
>  `-recurse` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut, geçerli dizindeki tüm Visual Basic dosyaları derler.  
  
```console
vbc *.vb  
```  
  
 Aşağıdaki komut, tüm Visual Basic dosyaları derler `Test\ABC` dizin ve altındaki dizinleri ve ardından oluşturur `Test.ABC.dll`.  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
