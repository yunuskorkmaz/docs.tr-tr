---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 405b557568a736de3ddc3b51e265261222613131
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403037"
---
# <a name="-verbose"></a>-verbose
Derleyicinin ayrıntılı durum ve hata iletileri oluşturmasına neden olur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
 `+`&#124;`-`  
 İsteğe bağlı. Belirtme, `-verbose` `-verbose+` derleyicinin ayrıntılı iletiler yaymasına neden olan, belirtilerek aynı şekilde belirlenir. Bu seçenek için varsayılan değer `-verbose-` .  
  
## <a name="remarks"></a>Açıklamalar  
 `-verbose`Seçeneği derleyici tarafından verilen toplam hata sayısı, bir modül tarafından hangi derlemelerin yüklendiğini raporlar ve şu anda derlenen dosyaları görüntüler.  
  
> [!NOTE]
> `-verbose`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `In.vb` ve derleyicinin ayrıntılı durum bilgilerini görüntülemesi için yönlendirir.  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
