---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: e70496b552ced8e07cbe3cde34cda377d94da9f4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188423"
---
# <a name="-verbose"></a>-verbose
Ayrıntılı durum ve hata iletileri oluşturmak derleyicinin neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 İsteğe bağlı. Belirtme `-verbose` belirtmekle aynı `-verbose+`, ayrıntılı iletiler dönüştüğünde derleyicinin neden olur. Bu seçenek için varsayılan değer `-verbose-`.  
  
## <a name="remarks"></a>Açıklamalar  
 `-verbose` Seçeneği derleyici tarafından verilen hatalarının toplam sayısını hakkında bilgi, hangi derlemelerin modülü tarafından yüklenen raporları ve hangi dosyaların şu anda derlenen görüntüler.  
  
> [!NOTE]
>  `-verbose` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yapılırken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod derlenir `In.vb` ve ayrıntılı durum bilgilerini görüntülemek için derleyicinin yönlendirir.  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
