---
title: "Nasıl yapılır: İçeriğini alma Visual Basic'te Belgelerim dizini"
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: 6313ebd190a6cee8a697399e2e77b63d8c43db2e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602591"
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a>Nasıl yapılır: İçeriğini alma Visual Basic'te Belgelerim dizini
<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> Nesne, birçok okuma için kullanılabilir **tüm kullanıcılar** dizinleri gibi **Belgelerim** veya **Masaüstü**.  
  
### <a name="to-read-from-the-my-documents-folder"></a>Belgelerim klasöründeki okumak için  
  
-   Kullanım `ReadAllText` belirli bir dizindeki her bir dosyadan metin okuma için yöntemi. Aşağıdaki kod bir dizin ve dosya belirtir ve ardından `ReadAllText` adlı dizeye okunacak `patients`.  
  
     [!code-vb[VbVbcnMyFileSystem#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-retrieve-the-contents-of-the-my-documents-directory_1.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
