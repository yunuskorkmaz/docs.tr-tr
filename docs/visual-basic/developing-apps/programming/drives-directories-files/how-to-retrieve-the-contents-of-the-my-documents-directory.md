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
ms.locfileid: "33583233"
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="4b276-102">Nasıl Yapılır: Visual Basic'te Belgelerim Dizini İçeriğini Alma</span><span class="sxs-lookup"><span data-stu-id="4b276-102">How to: Retrieve the Contents of the My Documents Directory in Visual Basic</span></span>
<span data-ttu-id="4b276-103"><xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> Nesne ait birçok özellikten okumak için kullanılabilecek **tüm kullanıcılar** dizinleri gibi **Belgelerim** veya **Masaüstü**.</span><span class="sxs-lookup"><span data-stu-id="4b276-103">The <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> object can be used to read from many of the **All Users** directories, such as **My Documents** or **Desktop**.</span></span>  
  
### <a name="to-read-from-the-my-documents-folder"></a><span data-ttu-id="4b276-104">Belgelerim klasöründen okunamıyor</span><span class="sxs-lookup"><span data-stu-id="4b276-104">To read from the My Documents folder</span></span>  
  
-   <span data-ttu-id="4b276-105">Kullanım `ReadAllText` yöntemi belirli bir dizin her dosyasından metin okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="4b276-105">Use the `ReadAllText` method to read the text from each file in a specific directory.</span></span> <span data-ttu-id="4b276-106">Aşağıdaki kod bir dizin ve dosya belirtir ve ardından `ReadAllText` adlı dizeye okumak için `patients`.</span><span class="sxs-lookup"><span data-stu-id="4b276-106">The following code specifies a directory and file and then uses `ReadAllText` to read them into the string named `patients`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-retrieve-the-contents-of-the-my-documents-directory_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4b276-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4b276-107">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
