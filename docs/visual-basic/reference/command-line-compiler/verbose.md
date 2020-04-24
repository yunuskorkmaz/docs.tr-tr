---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 8c5bc1d2ce331b8fe9461f91d64fbeab5a070b59
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004981"
---
# <a name="-verbose"></a>-verbose
Derleyicinin ayrıntılı durum ve hata iletileri oluşturmasına neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `+`&#124;`-`  
 İsteğe bağlı. Belirtme `-verbose` , derleyicinin ayrıntılı iletiler yaymasına neden olan, belirtilerek `-verbose+`aynı şekilde belirlenir. Bu seçenek için varsayılan değer `-verbose-`.  
  
## <a name="remarks"></a>Açıklamalar  
 `-verbose` Seçeneği derleyici tarafından verilen toplam hata sayısı, bir modül tarafından hangi derlemelerin yüklendiğini raporlar ve şu anda derlenen dosyaları görüntüler.  
  
> [!NOTE]
> Bu `-verbose` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `In.vb` ve derleyicinin ayrıntılı durum bilgilerini görüntülemesi için yönlendirir.  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
