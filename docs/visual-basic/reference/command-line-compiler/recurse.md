---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 4281c7bf5a7972d323e1e649aaef437c7ee901ff
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956272"
---
# <a name="-recurse"></a>-recurse
Belirtilen dizinin ya da proje dizininin tüm alt dizinlerindeki kaynak kodu dosyalarını derler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>Arguments  
 `dir`  
 İsteğe bağlı. Aramanın başlamasını istediğiniz dizin. Belirtilmemişse, arama proje dizininde başlar.  
  
 `file`  
 Gerekli. Aranacak dosya (lar). Joker karakterlere izin verilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanarak `-recurse`proje dizinindeki tüm eşleşen dosyaları derlemek için dosya adında joker karakterler kullanabilirsiniz. Çıkış dosyası adı belirtilmemişse, derleyici, çıktı dosyasının adını işlenen ilk girdi dosyasında temel alır. Bu genellikle alfabetik olarak görüntülendiklerinde derlenen dosyalar listesindeki ilk dosyadır. Bu nedenle, `-out` seçeneğini kullanarak bir çıkış dosyası belirtmek en iyisidir.  
  
> [!NOTE]
> Bu `-recurse` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut, geçerli dizindeki tüm Visual Basic dosyalarını derler.  
  
```console
vbc *.vb  
```  
  
 Aşağıdaki komut `Test\ABC` dizindeki tüm Visual Basic dosyalarını ve altındaki tüm dizinleri derler ve sonra üretir `Test.ABC.dll`.  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
