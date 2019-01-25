---
title: Gömülü birlikte çalışma derlemesine bir başvuru oluşturuldu &#39; &lt;assembly1&gt; &#39; derlemeden derlemeye dolaylı başvurudan dolayı &#39; &lt;assembly2&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
ms.openlocfilehash: fe04742e0a3be5e1d19ab4017e55f2293988a671
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560028"
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-39ltassembly1gt39-because-of-an-indirect-reference-to-that-assembly-from-assembly-39ltassembly2gt39"></a>Gömülü birlikte çalışma derlemesine bir başvuru oluşturuldu &#39; &lt;assembly1&gt; &#39; derlemeden derlemeye dolaylı başvurudan dolayı &#39; &lt;assembly2&gt;&#39;
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
