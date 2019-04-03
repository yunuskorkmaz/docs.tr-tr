---
title: "Nasıl yapılır: İçeriğini alma Visual Basic'te Belgelerim dizini"
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: fe98d3e92726dc6c4ed576ef989d968852c846d6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821835"
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="0d5b9-102">Nasıl yapılır: İçeriğini alma Visual Basic'te Belgelerim dizini</span><span class="sxs-lookup"><span data-stu-id="0d5b9-102">How to: Retrieve the Contents of the My Documents Directory in Visual Basic</span></span>
<span data-ttu-id="0d5b9-103"><xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> Nesne, birçok okuma için kullanılabilir **tüm kullanıcılar** dizinleri gibi **Belgelerim** veya **Masaüstü**.</span><span class="sxs-lookup"><span data-stu-id="0d5b9-103">The <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> object can be used to read from many of the **All Users** directories, such as **My Documents** or **Desktop**.</span></span>  
  
### <a name="to-read-from-the-my-documents-folder"></a><span data-ttu-id="0d5b9-104">Belgelerim klasöründeki okumak için</span><span class="sxs-lookup"><span data-stu-id="0d5b9-104">To read from the My Documents folder</span></span>  
  
-   <span data-ttu-id="0d5b9-105">Kullanım `ReadAllText` belirli bir dizindeki her bir dosyadan metin okuma için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0d5b9-105">Use the `ReadAllText` method to read the text from each file in a specific directory.</span></span> <span data-ttu-id="0d5b9-106">Aşağıdaki kod bir dizin ve dosya belirtir ve ardından `ReadAllText` adlı dizeye okunacak `patients`.</span><span class="sxs-lookup"><span data-stu-id="0d5b9-106">The following code specifies a directory and file and then uses `ReadAllText` to read them into the string named `patients`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="0d5b9-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d5b9-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
