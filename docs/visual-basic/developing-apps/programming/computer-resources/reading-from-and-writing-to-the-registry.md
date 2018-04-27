---
title: Kayıt Defterini Okuma ve Yazma (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a207b169e267fbcaccd46f7240d81afb3db27a8c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a><span data-ttu-id="4617d-102">Kayıt Defterini Okuma ve Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4617d-102">Reading from and Writing to the Registry (Visual Basic)</span></span>
<span data-ttu-id="4617d-103">Bu konuda, görev ve kayıt defteri ile ilişkili kavramsal konuları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4617d-103">This topic describes task and conceptual topics that are associated with the registry.</span></span>  
  
 <span data-ttu-id="4617d-104">Visual Basic'te programlama, Visual Basic veya .NET Framework'ün kayıt defteri sınıflar tarafından sağlanan işlevleri yoluyla kayıt defterine erişim seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4617d-104">When programming in Visual Basic, you can choose to access the registry by means of either the functions provided by Visual Basic or the registry classes of the .NET Framework.</span></span> <span data-ttu-id="4617d-105">Kayıt defteri bilgileri işletim sisteminden bilgilerinin yanı sıra bir makinede barındırılan uygulamalardan barındırır.</span><span class="sxs-lookup"><span data-stu-id="4617d-105">The registry hosts information from the operating system as well as information from applications hosted on the machine.</span></span> <span data-ttu-id="4617d-106">Kayıt defteri ile çalışma sistem kaynaklarına uygun erişime izin vererek güvenliği tehlikeye atabilir veya bilgi korumalı.</span><span class="sxs-lookup"><span data-stu-id="4617d-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4617d-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4617d-107">In This Section</span></span>  
 [<span data-ttu-id="4617d-108">Nasıl Yapılır: Kayıt Defteri Anahtarı Oluşturma ve Değerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="4617d-108">How to: Create a Registry Key and Set Its Value</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 <span data-ttu-id="4617d-109">Nasıl kullanılacağını açıklar `CreateSubKey` ve `SetValue` yöntemlerinin `My.Computer.Registry` bir kayıt defteri anahtarı oluşturun ve değerini ayarlama için nesne.</span><span class="sxs-lookup"><span data-stu-id="4617d-109">Describes how to use the `CreateSubKey` and `SetValue` methods of the `My.Computer.Registry` object to create a registry key and set its value.</span></span>  
  
 [<span data-ttu-id="4617d-110">Nasıl Yapılır: Kayıt Defteri Anahtarından Değer Okuma</span><span class="sxs-lookup"><span data-stu-id="4617d-110">How to: Read a Value from a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 <span data-ttu-id="4617d-111">Nasıl kullanılacağını açıklar `GetValue` yöntemi `My.Computer.Registry` kayıt defteri anahtarından değer okuma için nesne.</span><span class="sxs-lookup"><span data-stu-id="4617d-111">Describes how to use the `GetValue` method of the `My.Computer.Registry` object to read a value from a registry key.</span></span>  
  
 [<span data-ttu-id="4617d-112">Nasıl Yapılır: Kayıt Defteri Anahtarını Silme</span><span class="sxs-lookup"><span data-stu-id="4617d-112">How to: Delete a Registry Key</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 <span data-ttu-id="4617d-113">Nasıl kullanılacağını açıklar `DeleteSubKey` yöntemi `My.Computer.Registry.CurrentUser` özelliği bir kayıt defteri anahtarını silin.</span><span class="sxs-lookup"><span data-stu-id="4617d-113">Describes how to use the `DeleteSubKey` method of the `My.Computer.Registry.CurrentUser` property to delete a registry key.</span></span>  
  
 [<span data-ttu-id="4617d-114">Microsoft.Win32 Ad Alanını Kullanarak Kayıt Defterini Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="4617d-114">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 <span data-ttu-id="4617d-115">Nasıl kullanılacağını açıklar `Registry` ve `RegistryKey` sınıfları [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] kayıt defterine erişemedi.</span><span class="sxs-lookup"><span data-stu-id="4617d-115">Describes how to use the `Registry` and `RegistryKey` classes of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] to access the registry.</span></span>  
  
 [<span data-ttu-id="4617d-116">Güvenlik ve Kayıt Defteri</span><span class="sxs-lookup"><span data-stu-id="4617d-116">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 <span data-ttu-id="4617d-117">Kayıt defteriyle ilgili güvenlik konuları anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4617d-117">Discusses security issues involving the registry.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4617d-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="4617d-118">Related Sections</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <span data-ttu-id="4617d-119">Listeler ve üyeleri açıklar `My.Computer.Registry` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="4617d-119">Lists and explains members of the `My.Computer.Registry` object.</span></span>  
  
 <xref:Microsoft.Win32.Registry>  
 <span data-ttu-id="4617d-120">Genel bir bakış sunar `Registry` tek tek anahtarları ve üyeleri bağlantılarıyla birlikte sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4617d-120">Presents an overview of the `Registry` class, along with links to individual keys and members.</span></span>
