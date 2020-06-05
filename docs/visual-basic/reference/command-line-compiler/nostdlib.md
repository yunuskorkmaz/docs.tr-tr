---
title: -nostdlib
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 0934799853323110e73087ba6d8975c30f84d8f7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387718"
---
# <a name="-nostdlib-visual-basic"></a>-nostdlib (Visual Basic)
Derleyicinin standart kitaplıklara otomatik olarak başvurmasına neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `-nostdlib`Seçeneği, System. dll derlemesine otomatik başvuruyu kaldırır ve derleyicinin Vbc. rsp dosyasını okumasını önler. Vbc. exe dosyası ile aynı dizinde bulunan Vbc. rsp dosyası, yaygın olarak kullanılan .NET Framework derlemelerine başvurur ve `System` ve `Microsoft.VisualBasic` ad alanlarını içeri aktarır.  
  
> [!NOTE]
> Mscorlib. dll ve Microsoft. VisualBasic. dll derlemelerine her zaman başvurulur.  
  
> [!NOTE]
> `-nostdlib`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod `T2.vb` Standart kitaplıklara başvurulmadan derlenir. `_MYTYPE`Nesneyi kaldırmak için koşullu derleme sabitinin "Empty" dizesini ayarlamanız gerekir `My` .  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-noconfig](noconfig.md)
- [Visual Basic komut satırı derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
- [My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme](../../developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
