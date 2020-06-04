---
title: Kayıt Defterinden Okuma ve Kayıt Defterine Yazma
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
ms.openlocfilehash: bb400ef89edaa4eb743aee3a7f2cc5b9dfec4534
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360065"
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a><span data-ttu-id="913da-102">Kayıt Defterini Okuma ve Yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="913da-102">Reading from and Writing to the Registry (Visual Basic)</span></span>

<span data-ttu-id="913da-103">Bu konuda, kayıt defteriyle ilişkili görev ve kavramsal konular açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="913da-103">This topic describes task and conceptual topics that are associated with the registry.</span></span>  
  
 <span data-ttu-id="913da-104">Visual Basic programlamada, Visual Basic veya .NET Framework kayıt defteri sınıfları tarafından belirtilen işlevlere göre kayıt defterine erişmeyi seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="913da-104">When programming in Visual Basic, you can choose to access the registry by means of either the functions provided by Visual Basic or the registry classes of the .NET Framework.</span></span> <span data-ttu-id="913da-105">Kayıt defteri, işletim sisteminin bilgilerini ve makinede barındırılan uygulamalardan bilgileri barındırır.</span><span class="sxs-lookup"><span data-stu-id="913da-105">The registry hosts information from the operating system as well as information from applications hosted on the machine.</span></span> <span data-ttu-id="913da-106">Kayıt defteriyle çalışma, sistem kaynaklarına veya korunan bilgilere uygunsuz erişime izin vererek güvenliği tehlikeye atabilir.</span><span class="sxs-lookup"><span data-stu-id="913da-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="913da-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="913da-107">In This Section</span></span>  

 [<span data-ttu-id="913da-108">Nasıl yapılır: Kayıt Defteri Anahtarı Oluşturma ve Değerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="913da-108">How to: Create a Registry Key and Set Its Value</span></span>](how-to-create-a-registry-key-and-set-its-value.md)  
 <span data-ttu-id="913da-109">`CreateSubKey` `SetValue` `My.Computer.Registry` Bir kayıt defteri anahtarı oluşturmak ve değerini ayarlamak için nesnesinin ve yöntemlerinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="913da-109">Describes how to use the `CreateSubKey` and `SetValue` methods of the `My.Computer.Registry` object to create a registry key and set its value.</span></span>  
  
 [<span data-ttu-id="913da-110">Nasıl yapılır: Kayıt Defteri Anahtarından Değer Okuma</span><span class="sxs-lookup"><span data-stu-id="913da-110">How to: Read a Value from a Registry Key</span></span>](how-to-read-a-value-from-a-registry-key.md)  
 <span data-ttu-id="913da-111">`GetValue` `My.Computer.Registry` Bir kayıt defteri anahtarından bir değeri okumak için nesnesinin yönteminin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="913da-111">Describes how to use the `GetValue` method of the `My.Computer.Registry` object to read a value from a registry key.</span></span>  
  
 [<span data-ttu-id="913da-112">Nasıl yapılır: Kayıt Defteri Anahtarını Silme</span><span class="sxs-lookup"><span data-stu-id="913da-112">How to: Delete a Registry Key</span></span>](how-to-delete-a-registry-key.md)  
 <span data-ttu-id="913da-113">`DeleteSubKey` `My.Computer.Registry.CurrentUser` Bir kayıt defteri anahtarını silmek için özelliğinin yönteminin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="913da-113">Describes how to use the `DeleteSubKey` method of the `My.Computer.Registry.CurrentUser` property to delete a registry key.</span></span>  
  
 [<span data-ttu-id="913da-114">Microsoft.Win32 Ad Alanını Kullanarak Kayıt Defterini Okuma ve Yazma</span><span class="sxs-lookup"><span data-stu-id="913da-114">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace</span></span>](reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 <span data-ttu-id="913da-115">`Registry` `RegistryKey` Kayıt defterine erişmek için .NET Framework ve sınıflarının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="913da-115">Describes how to use the `Registry` and `RegistryKey` classes of the .NET Framework to access the registry.</span></span>  
  
 [<span data-ttu-id="913da-116">Güvenlik ve Kayıt Defteri</span><span class="sxs-lookup"><span data-stu-id="913da-116">Security and the Registry</span></span>](security-and-the-registry.md)  
 <span data-ttu-id="913da-117">Kayıt defteriyle ilgili güvenlik sorunlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="913da-117">Discusses security issues involving the registry.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="913da-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="913da-118">Related Sections</span></span>  

 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <span data-ttu-id="913da-119">Nesnesinin üyelerini listeler ve açıklar `My.Computer.Registry` .</span><span class="sxs-lookup"><span data-stu-id="913da-119">Lists and explains members of the `My.Computer.Registry` object.</span></span>  
  
 <xref:Microsoft.Win32.Registry>  
 <span data-ttu-id="913da-120">`Registry`Tek tek anahtarların ve üyelerin bağlantılarıyla birlikte sınıfına genel bir bakış sunar.</span><span class="sxs-lookup"><span data-stu-id="913da-120">Presents an overview of the `Registry` class, along with links to individual keys and members.</span></span>
