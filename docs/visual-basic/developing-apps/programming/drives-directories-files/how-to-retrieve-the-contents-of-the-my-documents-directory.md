---
title: 'Nasıl Yapılır: Belgelerim Dizini İçeriğini Alma'
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: cf4470020507c581999b9d72602ddb6e3e76ed74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334529"
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="aac5e-102">Nasıl Yapılır: Visual Basic'te Belgelerim Dizini İçeriğini Alma</span><span class="sxs-lookup"><span data-stu-id="aac5e-102">How to: Retrieve the Contents of the My Documents Directory in Visual Basic</span></span>

<span data-ttu-id="aac5e-103"><xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> Nesnesi, **Belgelerim** veya **masaüstlerim**gibi **tüm Kullanıcı** dizinlerinden okumak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aac5e-103">The <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> object can be used to read from many of the **All Users** directories, such as **My Documents** or **Desktop**.</span></span>  
  
### <a name="to-read-from-the-my-documents-folder"></a><span data-ttu-id="aac5e-104">Belgelerim klasöründen okumak için</span><span class="sxs-lookup"><span data-stu-id="aac5e-104">To read from the My Documents folder</span></span>  
  
- <span data-ttu-id="aac5e-105">Belirli bir `ReadAllText` dizindeki her bir dosyanın metnini okumak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="aac5e-105">Use the `ReadAllText` method to read the text from each file in a specific directory.</span></span> <span data-ttu-id="aac5e-106">Aşağıdaki kod, bir dizini ve dosyayı belirtir ve sonra bunları `ReadAllText` adlı `patients`dizeye okumak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="aac5e-106">The following code specifies a directory and file and then uses `ReadAllText` to read them into the string named `patients`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="aac5e-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aac5e-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
