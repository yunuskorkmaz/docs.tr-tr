---
title: "Nasıl Yapılır: Visual Basic'te Belgelerim Dizini İçeriğini Alma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3456984a697439a8c2ab7fb88f9f0f32d10cb0e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Belgelerim Dizini İçeriğini Alma
<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> Nesne ait birçok özellikten okumak için kullanılabilecek **tüm kullanıcılar** dizinleri gibi **Belgelerim** veya **Masaüstü**.  
  
### <a name="to-read-from-the-my-documents-folder"></a>Belgelerim klasöründen okunamıyor  
  
-   Kullanım `ReadAllText` yöntemi belirli bir dizin her dosyasından metin okunamıyor. Aşağıdaki kod bir dizin ve dosya belirtir ve ardından `ReadAllText` adlı dizeye okumak için `patients`.  
  
     [!code-vb[VbVbcnMyFileSystem#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-retrieve-the-contents-of-the-my-documents-directory_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
