---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 5b3899462af7c4aa8e0f77377a8d7485975f9867
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937267"
---
# <a name="-verbose"></a>-verbose
Derleyicinin ayrıntılı durum ve hata iletileri oluşturmasına neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 İsteğe bağlı. Belirtme `-verbose` , derleyicinin ayrıntılı iletiler yaymasına neden olan, belirtilerek `-verbose+`aynı şekilde belirlenir. Bu seçenek `-verbose-`için varsayılan değer.  
  
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
