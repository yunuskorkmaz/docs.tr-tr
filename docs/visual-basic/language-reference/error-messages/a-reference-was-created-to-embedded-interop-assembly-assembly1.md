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
ms.openlocfilehash: 058aa4891d05147756290affd60ea5fb260c33ef
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262958"
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-assembly1-because-of-an-indirect-reference-to-that-assembly-from-assembly-assembly2"></a>Gömülü birlikte çalışma derlemesine bir başvuru oluşturuldu '\<assembly1 >' derlemesinden derlemeye dolaylı başvurudan dolayı '\<assembly2 >'
Gömülü birlikte çalışma derlemesine bir başvuru oluşturuldu '\<assembly1 >' derlemesinden derlemeye dolaylı başvurudan dolayı '\<assembly2 >'. İki derlemeden birinde 'Embed Interop Types' özelliğini değiştirmeyi düşünün.  
  
 Sahip (assembly1) derlemeye bir başvuru eklediğiniz `Embed Interop Types` özelliğini `True`. Bu, derlemesinden birlikte çalışma tür bilgisini katıştırmak için derleyiciye. Ancak, başka bir derleme (assembly2) başvurulan de (assembly1) derlemeye başvuruyor ve sahip olduğundan bu derlemesinden birlikte çalışma tür bilgisini derleyici katıştırılamıyor `Embed Interop Types` özelliğini `False`.  
  
> [!NOTE]
>  Ayarı `Embed Interop Types` bir bütünleştirilmiş kod başvurusu özelliği `True` kullanarak derlemeye başvurmak için eşdeğer bir gruba `/link` komut satırı derleyicisi seçeneği.  
  
 **Hata Kimliği:** BC40059  
  
### <a name="to-address-this-warning"></a>Bu uyarıyı gidermek için  
  
-   Birlikte çalışma türünden bilgiler hem derlemeler için katıştırmak için `Embed Interop Types` assembly1 için yapılan tüm başvurular özelliği `True`.  
  
-   Bu uyarıyı kaldırmak için ayarlayabileceğiniz `Embed Interop Types` assembly1'özelliği `False`. Bu durumda, birlikte çalışma türünden bilgiler bir birincil birlikte çalışma derlemesi (PIA) tarafından sağlanır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [/ Link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md)
- [Yönetilmeyen Kod ile Birlikte Çalışma](../../../framework/interop/index.md)
