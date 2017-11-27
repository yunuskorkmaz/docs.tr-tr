---
title: "Bir başvuru katıştırılmış birlikte çalışma derlemesi & #39 oluşturuldu; &lt;assembly1&gt;& #39; bu derleme için dolaylı bir başvuru derleme & #39; nedeniyle&lt; assembly2&gt;& #39;"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bc2fbb044fc839aa24abf3dc1ea864457efb0653
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-39ltassembly1gt39-because-of-an-indirect-reference-to-that-assembly-from-assembly-39ltassembly2gt39"></a>Bir başvuru katıştırılmış birlikte çalışma derlemesi & #39 oluşturuldu; &lt;assembly1&gt;& #39; bu derleme için dolaylı bir başvuru derleme & #39; nedeniyle&lt; assembly2&gt;& #39;
Bir başvuru katıştırılmış birlikte çalışma derlemesi için oluşturulan '\<assembly1 >' o derleme dolaylı bir başvuru derlemesinden '\<assembly2 >'. Herhangi bir derleme üzerinde 'Birlikte çalışma türlerini katıştır' özelliği değiştirmeyi düşünün.  
  
 Bir derlemeye (assembly1) başvuru eklediğiniz `Embed Interop Types` özelliğini `True`. Bu bütünleştirilmiş birlikte çalışma tür bilgilerini katıştırma derleyiciye. Ancak, başka bir derleme (assembly2) başvurulan de bu derlemeye (assembly1) başvuruyor ve olduğundan bu derleme birlikte çalışma tür bilgilerini derleyici eklenemiyor `Embed Interop Types` özelliğini `False`.  
  
> [!NOTE]
>  Ayarlama `Embed Interop Types` derleme başvurusunun özellikte `True` kullanarak bütünleştirilmiş başvurma için eşdeğer bir gruba `/link` seçeneği için komut satırı derleyicisi.  
  
 **Hata Kimliği:** BC40059  
  
### <a name="to-address-this-warning"></a>Bu uyarıyı gidermek için  
  
-   Her iki derlemeler için birlikte çalışma türü bilgileri katıştırmak için `Embed Interop Types` assembly1 için yapılan tüm başvuruları özellikte `True`.  
  
-   Uyarıyı kaldırmak için ayarlayabileceğiniz `Embed Interop Types` assembly1'özelliğinin `False`. Bu durumda, birlikte çalışma türü bilgileri birincil birlikte çalışma derlemesi (PIA) tarafından sağlanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [/ Link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md)  
 [Birincil birlikte çalışma derlemeleri ile programlama](http://msdn.microsoft.com/en-us/306fa1d6-0703-4004-9e93-d0a57f1be81e)
