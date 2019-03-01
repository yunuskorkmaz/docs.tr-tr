---
title: "Nasıl yapılır: İçeriğini alma Visual Basic'te Belgelerim dizini"
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: 6d4e0bc7d300b2553d5286600cc65b7c494359b9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964193"
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a>Nasıl yapılır: İçeriğini alma Visual Basic'te Belgelerim dizini
<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> Nesne, birçok okuma için kullanılabilir **tüm kullanıcılar** dizinleri gibi **Belgelerim** veya **Masaüstü**.  
  
### <a name="to-read-from-the-my-documents-folder"></a>Belgelerim klasöründeki okumak için  
  
-   Kullanım `ReadAllText` belirli bir dizindeki her bir dosyadan metin okuma için yöntemi. Aşağıdaki kod bir dizin ve dosya belirtir ve ardından `ReadAllText` adlı dizeye okunacak `patients`.  
  
     [!code-vb[VbVbcnMyFileSystem#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
