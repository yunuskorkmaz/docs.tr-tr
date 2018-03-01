---
title: "&#39; &lt;özniteliği&gt;&#39; çünkü uygulanamaz GUID &#39; biçimi&lt; sayı&gt;&#39; doğru değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8ead07d12064dbe18a1e23d4d1343b1efba1b533
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="39ltattributegt39-cannot-be-applied-because-the-format-of-the-guid-39ltnumbergt39-is-not-correct"></a>&#39; &lt;özniteliği&gt;&#39; çünkü uygulanamaz GUID &#39; biçimi&lt; sayı&gt;&#39; doğru değil
A `COMClassAttribute` özniteliği bloğu için bir GUID düzgün biçime uymuyor bir genel benzersiz tanımlayıcı (GUID) belirtir. `COMClassAttribute`sınıfı, arabirimi ve oluşturma olay benzersiz şekilde tanımlamak için GUID'leri kullanır.  
  
 Bir GUID 16 biri ilk sekiz sayısal ve son sekiz ikili bayt oluşur. Uuidgen.exe gibi Microsoft yardımcı programlar tarafından oluşturulan ve alan ve zaman içinde benzersiz olması garanti edilmez.  
  
 **Hata Kimliği:** BC32500  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Doğru GUID veya GUID'leri COM nesnesi tanımlamak gerekli belirleyin.  
  
2.  GUID dizeleri için sunulan olun `COMClassAttribute` öznitelik blok düzgün kopyalanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Guid>  
[Öznitelikler genel bakış](../../../visual-basic/programming-guide/concepts/attributes/index.md)

