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
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="1176d-102">Nasıl yapılır: İçeriğini alma Visual Basic'te Belgelerim dizini</span><span class="sxs-lookup"><span data-stu-id="1176d-102">How to: Retrieve the Contents of the My Documents Directory in Visual Basic</span></span>
<span data-ttu-id="1176d-103"><xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> Nesne, birçok okuma için kullanılabilir **tüm kullanıcılar** dizinleri gibi **Belgelerim** veya **Masaüstü**.</span><span class="sxs-lookup"><span data-stu-id="1176d-103">The <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> object can be used to read from many of the **All Users** directories, such as **My Documents** or **Desktop**.</span></span>  
  
### <a name="to-read-from-the-my-documents-folder"></a><span data-ttu-id="1176d-104">Belgelerim klasöründeki okumak için</span><span class="sxs-lookup"><span data-stu-id="1176d-104">To read from the My Documents folder</span></span>  
  
-   <span data-ttu-id="1176d-105">Kullanım `ReadAllText` belirli bir dizindeki her bir dosyadan metin okuma için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1176d-105">Use the `ReadAllText` method to read the text from each file in a specific directory.</span></span> <span data-ttu-id="1176d-106">Aşağıdaki kod bir dizin ve dosya belirtir ve ardından `ReadAllText` adlı dizeye okunacak `patients`.</span><span class="sxs-lookup"><span data-stu-id="1176d-106">The following code specifies a directory and file and then uses `ReadAllText` to read them into the string named `patients`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-retrieve-the-contents-of-the-my-documents-directory_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1176d-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1176d-107">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
