---
title: Kayıt Defterini Okuma ve Yazma
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
ms.openlocfilehash: 89db9ef9db4235c069d6239d32e4f8679fbabf0b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349758"
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a><span data-ttu-id="3d2d5-102">Kayıt Defterini Okuma ve Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d2d5-102">Reading from and Writing to the Registry (Visual Basic)</span></span>

<span data-ttu-id="3d2d5-103">This topic describes task and conceptual topics that are associated with the registry.</span><span class="sxs-lookup"><span data-stu-id="3d2d5-103">This topic describes task and conceptual topics that are associated with the registry.</span></span>  
  
 <span data-ttu-id="3d2d5-104">When programming in Visual Basic, you can choose to access the registry by means of either the functions provided by Visual Basic or the registry classes of the .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3d2d5-104">When programming in Visual Basic, you can choose to access the registry by means of either the functions provided by Visual Basic or the registry classes of the .NET Framework.</span></span> <span data-ttu-id="3d2d5-105">The registry hosts information from the operating system as well as information from applications hosted on the machine.</span><span class="sxs-lookup"><span data-stu-id="3d2d5-105">The registry hosts information from the operating system as well as information from applications hosted on the machine.</span></span> <span data-ttu-id="3d2d5-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span><span class="sxs-lookup"><span data-stu-id="3d2d5-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3d2d5-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3d2d5-107">In This Section</span></span>  

 [<span data-ttu-id="3d2d5-108">Nasıl Yapılır: Kayıt Defteri Anahtarı Oluşturma ve Değerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="3d2d5-108">How to: Create a Registry Key and Set Its Value</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 <span data-ttu-id="3d2d5-109">Describes how to use the `CreateSubKey` and `SetValue` methods of the `My.Computer.Registry` object to create a registry key and set its value.</span><span class="sxs-lookup"><span data-stu-id="3d2d5-109">Describes how to use the `CreateSubKey` and `SetValue` methods of the `My.Computer.Registry` object to create a registry key and set its value.</span></span>  
  
 [<span data-ttu-id="3d2d5-110">Nasıl Yapılır: Kayıt Defteri Anahtarından Değer Okuma</span><span class="sxs-lookup"><span data-stu-id="3d2d5-110">How to: Read a Value from a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 <span data-ttu-id="3d2d5-111">Describes how to use the `GetValue` method of the `My.Computer.Registry` object to read a value from a registry key.</span><span class="sxs-lookup"><span data-stu-id="3d2d5-111">Describes how to use the `GetValue` method of the `My.Computer.Registry` object to read a value from a registry key.</span></span>  
  
 [<span data-ttu-id="3d2d5-112">Nasıl Yapılır: Kayıt Defteri Anahtarını Silme</span><span class="sxs-lookup"><span data-stu-id="3d2d5-112">How to: Delete a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 <span data-ttu-id="3d2d5-113">Describes how to use the `DeleteSubKey` method of the `My.Computer.Registry.CurrentUser` property to delete a registry key.</span><span class="sxs-lookup"><span data-stu-id="3d2d5-113">Describes how to use the `DeleteSubKey` method of the `My.Computer.Registry.CurrentUser` property to delete a registry key.</span></span>  
  
 [<span data-ttu-id="3d2d5-114">Microsoft.Win32 Ad Alanını Kullanarak Kayıt Defterini Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="3d2d5-114">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 <span data-ttu-id="3d2d5-115">Describes how to use the `Registry` and `RegistryKey` classes of the .NET Framework to access the registry.</span><span class="sxs-lookup"><span data-stu-id="3d2d5-115">Describes how to use the `Registry` and `RegistryKey` classes of the .NET Framework to access the registry.</span></span>  
  
 [<span data-ttu-id="3d2d5-116">Güvenlik ve Kayıt Defteri</span><span class="sxs-lookup"><span data-stu-id="3d2d5-116">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 <span data-ttu-id="3d2d5-117">Discusses security issues involving the registry.</span><span class="sxs-lookup"><span data-stu-id="3d2d5-117">Discusses security issues involving the registry.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3d2d5-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="3d2d5-118">Related Sections</span></span>  

 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <span data-ttu-id="3d2d5-119">Lists and explains members of the `My.Computer.Registry` object.</span><span class="sxs-lookup"><span data-stu-id="3d2d5-119">Lists and explains members of the `My.Computer.Registry` object.</span></span>  
  
 <xref:Microsoft.Win32.Registry>  
 <span data-ttu-id="3d2d5-120">Presents an overview of the `Registry` class, along with links to individual keys and members.</span><span class="sxs-lookup"><span data-stu-id="3d2d5-120">Presents an overview of the `Registry` class, along with links to individual keys and members.</span></span>
