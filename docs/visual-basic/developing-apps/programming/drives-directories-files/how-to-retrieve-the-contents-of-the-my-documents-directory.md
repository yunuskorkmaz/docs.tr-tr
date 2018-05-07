---
title: "Nasıl Yapılır: Visual Basic'te Belgelerim Dizini İçeriğini Alma"
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: 1d0536c65949dab7d431f3a4cb7b3293bddb7008
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Belgelerim Dizini İçeriğini Alma
<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> Nesne ait birçok özellikten okumak için kullanılabilecek **tüm kullanıcılar** dizinleri gibi **Belgelerim** veya **Masaüstü**.  
  
### <a name="to-read-from-the-my-documents-folder"></a>Belgelerim klasöründen okunamıyor  
  
-   Kullanım `ReadAllText` yöntemi belirli bir dizin her dosyasından metin okunamıyor. Aşağıdaki kod bir dizin ve dosya belirtir ve ardından `ReadAllText` adlı dizeye okumak için `patients`.  
  
     [!code-vb[VbVbcnMyFileSystem#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-retrieve-the-contents-of-the-my-documents-directory_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
