---
title: "Kayıt Defterini Okuma ve Yazma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: db564b428d585829b220674271f4636bfcc68562
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a><span data-ttu-id="c1b49-102">Kayıt Defterini Okuma ve Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1b49-102">Reading from and Writing to the Registry (Visual Basic)</span></span>
<span data-ttu-id="c1b49-103">Bu konuda, görev ve kayıt defteri ile ilişkili kavramsal konuları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c1b49-103">This topic describes task and conceptual topics that are associated with the registry.</span></span>  
  
 <span data-ttu-id="c1b49-104">Programlama zaman [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], kayıt defteri tarafından sağlanan işlevleri yoluyla erişmek seçebileceğiniz [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] veya .NET Framework'ün kayıt defteri sınıfları.</span><span class="sxs-lookup"><span data-stu-id="c1b49-104">When programming in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], you can choose to access the registry by means of either the functions provided by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] or the registry classes of the .NET Framework.</span></span> <span data-ttu-id="c1b49-105">Kayıt defteri bilgileri işletim sisteminden bilgilerinin yanı sıra bir makinede barındırılan uygulamalardan barındırır.</span><span class="sxs-lookup"><span data-stu-id="c1b49-105">The registry hosts information from the operating system as well as information from applications hosted on the machine.</span></span> <span data-ttu-id="c1b49-106">Kayıt defteri ile çalışma sistem kaynaklarına uygun erişime izin vererek güvenliği tehlikeye atabilir veya bilgi korumalı.</span><span class="sxs-lookup"><span data-stu-id="c1b49-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c1b49-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c1b49-107">In This Section</span></span>  
 [<span data-ttu-id="c1b49-108">Nasıl yapılır: bir kayıt defteri anahtarı oluşturun ve değerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="c1b49-108">How to: Create a Registry Key and Set Its Value</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 <span data-ttu-id="c1b49-109">Nasıl kullanılacağını açıklar `CreateSubKey` ve `SetValue` yöntemlerinin `My.Computer.Registry` bir kayıt defteri anahtarı oluşturun ve değerini ayarlama için nesne.</span><span class="sxs-lookup"><span data-stu-id="c1b49-109">Describes how to use the `CreateSubKey` and `SetValue` methods of the `My.Computer.Registry` object to create a registry key and set its value.</span></span>  
  
 [<span data-ttu-id="c1b49-110">Nasıl yapılır: bir kayıt defteri anahtarından değer okuma</span><span class="sxs-lookup"><span data-stu-id="c1b49-110">How to: Read a Value from a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 <span data-ttu-id="c1b49-111">Nasıl kullanılacağını açıklar `GetValue` yöntemi `My.Computer.Registry` kayıt defteri anahtarından değer okuma için nesne.</span><span class="sxs-lookup"><span data-stu-id="c1b49-111">Describes how to use the `GetValue` method of the `My.Computer.Registry` object to read a value from a registry key.</span></span>  
  
 [<span data-ttu-id="c1b49-112">Nasıl yapılır: bir kayıt defteri anahtarını silme</span><span class="sxs-lookup"><span data-stu-id="c1b49-112">How to: Delete a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 <span data-ttu-id="c1b49-113">Nasıl kullanılacağını açıklar `DeleteSubKey` yöntemi `My.Computer.Registry.CurrentUser` özelliği bir kayıt defteri anahtarını silin.</span><span class="sxs-lookup"><span data-stu-id="c1b49-113">Describes how to use the `DeleteSubKey` method of the `My.Computer.Registry.CurrentUser` property to delete a registry key.</span></span>  
  
 [<span data-ttu-id="c1b49-114">Okuma ve yazma Microsoft.Win32 Namespace kullanarak kayıt defteri</span><span class="sxs-lookup"><span data-stu-id="c1b49-114">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 <span data-ttu-id="c1b49-115">Nasıl kullanılacağını açıklar `Registry` ve `RegistryKey` sınıfları [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kayıt defterine erişemedi.</span><span class="sxs-lookup"><span data-stu-id="c1b49-115">Describes how to use the `Registry` and `RegistryKey` classes of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] to access the registry.</span></span>  
  
 [<span data-ttu-id="c1b49-116">Güvenlik ve kayıt defteri</span><span class="sxs-lookup"><span data-stu-id="c1b49-116">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 <span data-ttu-id="c1b49-117">Kayıt defteriyle ilgili güvenlik konuları anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c1b49-117">Discusses security issues involving the registry.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c1b49-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="c1b49-118">Related Sections</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <span data-ttu-id="c1b49-119">Listeler ve üyeleri açıklar `My.Computer.Registry` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c1b49-119">Lists and explains members of the `My.Computer.Registry` object.</span></span>  
  
 <xref:Microsoft.Win32.Registry>  
 <span data-ttu-id="c1b49-120">Genel bir bakış sunar `Registry` tek tek anahtarları ve üyeleri bağlantılarıyla birlikte sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c1b49-120">Presents an overview of the `Registry` class, along with links to individual keys and members.</span></span>
