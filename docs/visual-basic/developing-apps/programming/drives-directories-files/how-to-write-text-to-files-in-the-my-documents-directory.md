---
title: 'Nasıl Yapılır: Belgelerim Dizinindeki Dosyalara Metin Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: bc62f2bc63a2ea185b8ea4c8d271dd28d347d6f0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334519"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="b3d49-102">Nasıl Yapılır: Visual Basic'te Belgelerim Dizinindeki Dosyalara Metin Yazma</span><span class="sxs-lookup"><span data-stu-id="b3d49-102">How to: Write Text to Files in the My Documents Directory in Visual Basic</span></span>

<span data-ttu-id="b3d49-103">The `My.Computer.FileSystem.SpecialDirectories` object allows you to access special directories, such as the **MyDocuments** directory.</span><span class="sxs-lookup"><span data-stu-id="b3d49-103">The `My.Computer.FileSystem.SpecialDirectories` object allows you to access special directories, such as the **MyDocuments** directory.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="b3d49-104">Yordam</span><span class="sxs-lookup"><span data-stu-id="b3d49-104">Procedure</span></span>  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a><span data-ttu-id="b3d49-105">To write new text files in the My Documents directory</span><span class="sxs-lookup"><span data-stu-id="b3d49-105">To write new text files in the My Documents directory</span></span>  
  
1. <span data-ttu-id="b3d49-106">Use the `My.Computer.FileSystem.SpecialDirectories.MyDocuments` property to supply the path.</span><span class="sxs-lookup"><span data-stu-id="b3d49-106">Use the `My.Computer.FileSystem.SpecialDirectories.MyDocuments` property to supply the path.</span></span>  
  
     [!code-vb[VbFileIOWrite#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#1)]  
  
2. <span data-ttu-id="b3d49-107">Use the `WriteAllText` method to write text to the specified file.</span><span class="sxs-lookup"><span data-stu-id="b3d49-107">Use the `WriteAllText` method to write text to the specified file.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="b3d49-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3d49-108">Example</span></span>  

 [!code-vb[VbFileIOWrite#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b3d49-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b3d49-109">Compiling the Code</span></span>  

 <span data-ttu-id="b3d49-110">Replace `test.txt` with the name of the file you want to write to.</span><span class="sxs-lookup"><span data-stu-id="b3d49-110">Replace `test.txt` with the name of the file you want to write to.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b3d49-111">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="b3d49-111">Robust Programming</span></span>  

 <span data-ttu-id="b3d49-112">This code rethrows all the exceptions that may occur when writing text to the file.</span><span class="sxs-lookup"><span data-stu-id="b3d49-112">This code rethrows all the exceptions that may occur when writing text to the file.</span></span> <span data-ttu-id="b3d49-113">You can reduce the likelihood of exceptions by using Windows Forms controls such as the [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) and the [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) components that limit the user choices to valid file names.</span><span class="sxs-lookup"><span data-stu-id="b3d49-113">You can reduce the likelihood of exceptions by using Windows Forms controls such as the [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) and the [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) components that limit the user choices to valid file names.</span></span> <span data-ttu-id="b3d49-114">Using these controls is not foolproof, however.</span><span class="sxs-lookup"><span data-stu-id="b3d49-114">Using these controls is not foolproof, however.</span></span> <span data-ttu-id="b3d49-115">The file system can change between the time the user selects a file and the time that the code executes.</span><span class="sxs-lookup"><span data-stu-id="b3d49-115">The file system can change between the time the user selects a file and the time that the code executes.</span></span> <span data-ttu-id="b3d49-116">Exception handling is therefore nearly always necessary when with working with files.</span><span class="sxs-lookup"><span data-stu-id="b3d49-116">Exception handling is therefore nearly always necessary when with working with files.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b3d49-117">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="b3d49-117">.NET Framework Security</span></span>  

 <span data-ttu-id="b3d49-118">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span><span class="sxs-lookup"><span data-stu-id="b3d49-118">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="b3d49-119">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="b3d49-119">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
 <span data-ttu-id="b3d49-120">This example creates a new file.</span><span class="sxs-lookup"><span data-stu-id="b3d49-120">This example creates a new file.</span></span> <span data-ttu-id="b3d49-121">If an application needs to create a file, that application needs Create permission for the folder.</span><span class="sxs-lookup"><span data-stu-id="b3d49-121">If an application needs to create a file, that application needs Create permission for the folder.</span></span> <span data-ttu-id="b3d49-122">Permissions are set using access control lists.</span><span class="sxs-lookup"><span data-stu-id="b3d49-122">Permissions are set using access control lists.</span></span> <span data-ttu-id="b3d49-123">If the file already exists, the application needs only Write permission, a lesser privilege.</span><span class="sxs-lookup"><span data-stu-id="b3d49-123">If the file already exists, the application needs only Write permission, a lesser privilege.</span></span> <span data-ttu-id="b3d49-124">Where possible, it is more secure to create the file during deployment, and only grant Read privileges to a single file, rather than to grant Create privileges for a folder.</span><span class="sxs-lookup"><span data-stu-id="b3d49-124">Where possible, it is more secure to create the file during deployment, and only grant Read privileges to a single file, rather than to grant Create privileges for a folder.</span></span> <span data-ttu-id="b3d49-125">Also, it is more secure to write data to user folders than to the root folder or the **Program Files** folder.</span><span class="sxs-lookup"><span data-stu-id="b3d49-125">Also, it is more secure to write data to user folders than to the root folder or the **Program Files** folder.</span></span> <span data-ttu-id="b3d49-126">For more information, see [ACL Technology Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b3d49-126">For more information, see [ACL Technology Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3d49-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3d49-127">See also</span></span>

- <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
