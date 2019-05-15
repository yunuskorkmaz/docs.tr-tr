---
title: Kayıt Defterini Okuma ve Yazma (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
ms.openlocfilehash: fcc13d82a2b27221c13f9277585c21196b47003d
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591470"
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a><span data-ttu-id="9e07f-102">Kayıt Defterini Okuma ve Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e07f-102">Reading from and Writing to the Registry (Visual Basic)</span></span>
<span data-ttu-id="9e07f-103">Bu konuda, görev ve kayıt defteri ile ilişkili olan kavramsal konular açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9e07f-103">This topic describes task and conceptual topics that are associated with the registry.</span></span>  
  
 <span data-ttu-id="9e07f-104">Visual Basic'te programlama, Visual Basic veya .NET Framework'ün kayıt defteri sınıfları tarafından sağlanan işlevleri yoluyla kayıt defterine erişim seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e07f-104">When programming in Visual Basic, you can choose to access the registry by means of either the functions provided by Visual Basic or the registry classes of the .NET Framework.</span></span> <span data-ttu-id="9e07f-105">Kayıt defteri konakların bilgilerini makinede barındırılan uygulamalardan bilgi yanı sıra işletim sistemi.</span><span class="sxs-lookup"><span data-stu-id="9e07f-105">The registry hosts information from the operating system as well as information from applications hosted on the machine.</span></span> <span data-ttu-id="9e07f-106">Kayıt defteri ile çalışma, sistem kaynakları için uygun olmayan erişimine izin vererek güvenliği tehlikeye atabilir veya korumalı bilgileri.</span><span class="sxs-lookup"><span data-stu-id="9e07f-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9e07f-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9e07f-107">In This Section</span></span>  
 [<span data-ttu-id="9e07f-108">Nasıl yapılır: Bir kayıt defteri anahtarı oluşturma ve değerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="9e07f-108">How to: Create a Registry Key and Set Its Value</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 <span data-ttu-id="9e07f-109">Nasıl kullanılacağını açıklar `CreateSubKey` ve `SetValue` yöntemlerinin `My.Computer.Registry` nesne bir kayıt defteri anahtarı oluşturma ve değerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9e07f-109">Describes how to use the `CreateSubKey` and `SetValue` methods of the `My.Computer.Registry` object to create a registry key and set its value.</span></span>  
  
 [<span data-ttu-id="9e07f-110">Nasıl yapılır: Kayıt defteri anahtarından değer okuma</span><span class="sxs-lookup"><span data-stu-id="9e07f-110">How to: Read a Value from a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 <span data-ttu-id="9e07f-111">Nasıl kullanılacağını açıklar `GetValue` yöntemi `My.Computer.Registry` kayıt defteri anahtarından değer okuma için nesne.</span><span class="sxs-lookup"><span data-stu-id="9e07f-111">Describes how to use the `GetValue` method of the `My.Computer.Registry` object to read a value from a registry key.</span></span>  
  
 [<span data-ttu-id="9e07f-112">Nasıl yapılır: Bir kayıt defteri anahtarını silme</span><span class="sxs-lookup"><span data-stu-id="9e07f-112">How to: Delete a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 <span data-ttu-id="9e07f-113">Nasıl kullanılacağını açıklar `DeleteSubKey` yöntemi `My.Computer.Registry.CurrentUser` özelliği bir kayıt defteri anahtarını silin.</span><span class="sxs-lookup"><span data-stu-id="9e07f-113">Describes how to use the `DeleteSubKey` method of the `My.Computer.Registry.CurrentUser` property to delete a registry key.</span></span>  
  
 [<span data-ttu-id="9e07f-114">Microsoft.Win32 Ad Alanını Kullanarak Kayıt Defterini Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="9e07f-114">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 <span data-ttu-id="9e07f-115">Nasıl kullanılacağını açıklar `Registry` ve `RegistryKey` kayıt defterine erişim için .NET Framework'ün sınıfları.</span><span class="sxs-lookup"><span data-stu-id="9e07f-115">Describes how to use the `Registry` and `RegistryKey` classes of the .NET Framework to access the registry.</span></span>  
  
 [<span data-ttu-id="9e07f-116">Güvenlik ve Kayıt Defteri</span><span class="sxs-lookup"><span data-stu-id="9e07f-116">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 <span data-ttu-id="9e07f-117">Kayıt defteriyle ilgili güvenlik sorunları açıklar.</span><span class="sxs-lookup"><span data-stu-id="9e07f-117">Discusses security issues involving the registry.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9e07f-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="9e07f-118">Related Sections</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <span data-ttu-id="9e07f-119">Listeler ve üyelerini açıklar `My.Computer.Registry` nesne.</span><span class="sxs-lookup"><span data-stu-id="9e07f-119">Lists and explains members of the `My.Computer.Registry` object.</span></span>  
  
 <xref:Microsoft.Win32.Registry>  
 <span data-ttu-id="9e07f-120">Genel bir bakış sunan `Registry` bireysel anahtarları ve üyelerine bağlantılarıyla birlikte bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="9e07f-120">Presents an overview of the `Registry` class, along with links to individual keys and members.</span></span>
