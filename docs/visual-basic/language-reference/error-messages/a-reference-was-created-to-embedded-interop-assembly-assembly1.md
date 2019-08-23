---
title: "'<assembly1>' derlemesinden '<assembly2>' katıştırılmış birlikte çalışma derlemesine dolaylı bir başvuru bulunduğundan, bu birlikte çalışma derlemesine bir başvuru oluşturuldu"
ms.date: 07/20/2015
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
ms.openlocfilehash: 0f7a136abb0e63e4b139b87c8f18ae3fcb99dbf9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947758"
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-assembly1-because-of-an-indirect-reference-to-that-assembly-from-assembly-assembly2"></a>\<'\<Assembly2 > ' derlemesinden bu derlemeye dolaylı bir başvuru olduğundan, ' Assembly1 > ' katıştırılmış birlikte çalışma derlemesine bir başvuru oluşturuldu
\<'\<Assembly2 > ' derlemesinden bu derlemeye dolaylı bir başvuru olduğundan, ' Assembly1 > ' katıştırılmış birlikte çalışma derlemesine bir başvuru oluşturuldu. Herhangi bir derlemede ' birlikte çalışma türlerini katıştır ' özelliğini değiştirmeyi düşünün.  
  
 `Embed Interop Types` Özelliği olarak`True`ayarlanmış bir derlemeye (Assembly1) bir başvuru eklediniz. Bu, derleyiciye, bu derlemeden birlikte çalışma türü bilgilerini katıştırmasını söyler. Ancak, başvurmuş olduğunuz başka bir derleme (Assembly2) da bu derlemeye (Assembly1) başvurduğundan ve `Embed Interop Types` özelliği olarak ayarlandığı için `False`derleyici, birlikte çalışma türü bilgilerini bu derlemeden katıştıramaz.  
  
> [!NOTE]
> ' A bir derleme `True` başvurusu üzerinde `/link` özelliğininayarlanması,komutsatırıderleyicisiseçeneğikullanılarakderlemeyebaşvurulmayaeşdeğerdir.`Embed Interop Types`  
  
 **Hata KIMLIĞI:** BC40059  
  
### <a name="to-address-this-warning"></a>Bu uyarıyı çözmek için  
  
- Her iki derleme için birlikte çalışma türü bilgilerini eklemek için, `Embed Interop Types` Assembly1 öğesine tüm başvurularda özelliğini olarak `True`ayarlayın.  
  
- Uyarıyı kaldırmak için assembly1 `Embed Interop Types` özelliğini olarak `False`ayarlayabilirsiniz. Bu durumda, birlikte çalışma türü bilgileri bir birincil birlikte çalışma derlemesi (PIA) tarafından sağlanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [/Link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md)
- [Yönetilmeyen Kod ile Birlikte Çalışma](../../../framework/interop/index.md)
