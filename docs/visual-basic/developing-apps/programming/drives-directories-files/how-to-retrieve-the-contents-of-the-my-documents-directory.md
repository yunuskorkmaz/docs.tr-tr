---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Basic Belgelerim dizininin Içeriğini alma'
title: 'Nasıl yapılır: Belgelerim Dizini İçeriğini Alma'
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: e9e6ffc202332bd8d1849ef886fd4e7d6cc46a54
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797399"
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="4b24d-103">Nasıl Yapılır: Visual Basic'te Belgelerim Dizini İçeriğini Alma</span><span class="sxs-lookup"><span data-stu-id="4b24d-103">How to: Retrieve the Contents of the My Documents Directory in Visual Basic</span></span>

<span data-ttu-id="4b24d-104"><xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>Nesnesi, **Belgelerim veya Masaüstlerim** gibi **tüm Kullanıcı** dizinlerinden okumak için kullanılabilir. </span><span class="sxs-lookup"><span data-stu-id="4b24d-104">The <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> object can be used to read from many of the **All Users** directories, such as **My Documents** or **Desktop**.</span></span>  
  
### <a name="to-read-from-the-my-documents-folder"></a><span data-ttu-id="4b24d-105">Belgelerim klasöründen okumak için</span><span class="sxs-lookup"><span data-stu-id="4b24d-105">To read from the My Documents folder</span></span>  
  
- <span data-ttu-id="4b24d-106">`ReadAllText`Belirli bir dizindeki her bir dosyanın metnini okumak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4b24d-106">Use the `ReadAllText` method to read the text from each file in a specific directory.</span></span> <span data-ttu-id="4b24d-107">Aşağıdaki kod, bir dizini ve dosyayı belirtir ve sonra `ReadAllText` bunları adlı dizeye okumak için kullanır `patients` .</span><span class="sxs-lookup"><span data-stu-id="4b24d-107">The following code specifies a directory and file and then uses `ReadAllText` to read them into the string named `patients`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="4b24d-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b24d-108">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
