---
title: 'Nasıl yapılır: Access Control listesi girdileri ekleme veya kaldırma (yalnızca .NET Framework)'
ms.date: 01/14/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ACEs [.NET Framework]
- ACLs [.NET Framework]
- access control entries [.NET Framework]
- I/O [.NET Framework], access control list entries
- access control lists [.NET Framework]
ms.assetid: 53758b39-bd9b-4640-bb04-cad5ed8d0abf
ms.openlocfilehash: 49cbb27c1b9d7ae0b05077c7f4fe01a2dfe87ccb
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820806"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a><span data-ttu-id="6da99-102">Nasıl yapılır: Access Control listesi girdileri ekleme veya kaldırma (yalnızca .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="6da99-102">How to: Add or remove Access Control List entries (.NET Framework only)</span></span>

<span data-ttu-id="6da99-103">Bir dosya veya dizine Access Control List (ACL) girişi eklemek veya kaldırmak için, veya dizininden dosya ya da <xref:System.Security.AccessControl.FileSecurity> <xref:System.Security.AccessControl.DirectorySecurity> Dizin alın.</span><span class="sxs-lookup"><span data-stu-id="6da99-103">To add or remove Access Control List (ACL) entries to or from a file or directory, get the <xref:System.Security.AccessControl.FileSecurity> or <xref:System.Security.AccessControl.DirectorySecurity> object from the file or directory.</span></span> <span data-ttu-id="6da99-104">Nesneyi değiştirin ve ardından dosyayı veya dizini yeniden uygulayın.</span><span class="sxs-lookup"><span data-stu-id="6da99-104">Modify the object, and then apply it back to the file or directory.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a><span data-ttu-id="6da99-105">Dosyadan ACL girişi ekleme veya kaldırma</span><span class="sxs-lookup"><span data-stu-id="6da99-105">Add or remove an ACL entry from a file</span></span>  
  
1. <span data-ttu-id="6da99-106"><xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> <xref:System.Security.AccessControl.FileSecurity> Bir DOSYANıN geçerli ACL girdilerini içeren bir nesne almak için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="6da99-106">Call the <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.FileSecurity> object that contains the current ACL entries of a file.</span></span>  
  
2. <span data-ttu-id="6da99-107"><xref:System.Security.AccessControl.FileSecurity>1. adımdan döndürülen NESNEDEN ACL girişi ekleyin veya kaldırın.</span><span class="sxs-lookup"><span data-stu-id="6da99-107">Add or remove ACL entries from the <xref:System.Security.AccessControl.FileSecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="6da99-108">Değişiklikleri uygulamak için, <xref:System.Security.AccessControl.FileSecurity> nesneyi <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> yöntemine geçirin.</span><span class="sxs-lookup"><span data-stu-id="6da99-108">To apply the changes, pass the <xref:System.Security.AccessControl.FileSecurity> object to the <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a><span data-ttu-id="6da99-109">Bir dizinden ACL girişi ekleme veya kaldırma</span><span class="sxs-lookup"><span data-stu-id="6da99-109">Add or remove an ACL entry from a directory</span></span>  
  
1. <span data-ttu-id="6da99-110"><xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> <xref:System.Security.AccessControl.DirectorySecurity> Bir DIZININ geçerli ACL girdilerini içeren bir nesne almak için yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="6da99-110">Call the <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.DirectorySecurity> object that contains the current ACL entries of a directory.</span></span>  
  
2. <span data-ttu-id="6da99-111"><xref:System.Security.AccessControl.DirectorySecurity>1. adımdan döndürülen NESNEDEN ACL girişi ekleyin veya kaldırın.</span><span class="sxs-lookup"><span data-stu-id="6da99-111">Add or remove ACL entries from the <xref:System.Security.AccessControl.DirectorySecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="6da99-112">Değişiklikleri uygulamak için, <xref:System.Security.AccessControl.DirectorySecurity> nesneyi <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> yöntemine geçirin.</span><span class="sxs-lookup"><span data-stu-id="6da99-112">To apply the changes, pass the <xref:System.Security.AccessControl.DirectorySecurity> object to the <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6da99-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="6da99-113">Example</span></span>  
 <span data-ttu-id="6da99-114">Bu örneği çalıştırmak için geçerli bir kullanıcı veya grup hesabı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6da99-114">You must use a valid user or group account to run this example.</span></span> <span data-ttu-id="6da99-115">Örnek bir nesnesi kullanır <xref:System.IO.File> .</span><span class="sxs-lookup"><span data-stu-id="6da99-115">The example uses a <xref:System.IO.File> object.</span></span> <span data-ttu-id="6da99-116"><xref:System.IO.FileInfo>, <xref:System.IO.Directory> , Ve sınıfları için aynı yordamı kullanın <xref:System.IO.DirectoryInfo> .</span><span class="sxs-lookup"><span data-stu-id="6da99-116">Use the same procedure for the <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, and <xref:System.IO.DirectoryInfo> classes.</span></span>

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
