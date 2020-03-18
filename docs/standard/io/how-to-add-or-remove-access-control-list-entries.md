---
title: 'Nasıl yapılır: Erişim Denetim Listesi girişleri ekleme veya kaldırma (yalnızca.NET Framework)'
ms.date: 01/14/2019
ms.technology: dotnet-standard
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
ms.openlocfilehash: 5f41c518b8732adff95593cab29d7085adcc9ab3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708134"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a><span data-ttu-id="3304d-102">Nasıl yapılır: Erişim Denetim Listesi girişleri ekleme veya kaldırma (yalnızca.NET Framework)</span><span class="sxs-lookup"><span data-stu-id="3304d-102">How to: Add or remove Access Control List entries (.NET Framework only)</span></span>
<span data-ttu-id="3304d-103">Bir dosyaya veya dizine Erişim Denetim Listesi (ACL) girişlerini <xref:System.Security.AccessControl.FileSecurity> <xref:System.Security.AccessControl.DirectorySecurity> eklemek veya kaldırmak için, dosyadan veya dizinden veya nesneden veya dosyadan nesne alın.</span><span class="sxs-lookup"><span data-stu-id="3304d-103">To add or remove Access Control List (ACL) entries to or from a file or directory, get the <xref:System.Security.AccessControl.FileSecurity> or <xref:System.Security.AccessControl.DirectorySecurity> object from the file or directory.</span></span> <span data-ttu-id="3304d-104">Nesneyi değiştirin ve dosyaya veya dizine geri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="3304d-104">Modify the object, and then apply it back to the file or directory.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a><span data-ttu-id="3304d-105">Bir Dosyadan ACL girişi ekleme veya kaldırma</span><span class="sxs-lookup"><span data-stu-id="3304d-105">Add or remove an ACL entry from a file</span></span>  
  
1. <span data-ttu-id="3304d-106">Bir <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> dosyanın geçerli <xref:System.Security.AccessControl.FileSecurity> ACL girişlerini içeren bir nesneyi almak için yöntemi arayın.</span><span class="sxs-lookup"><span data-stu-id="3304d-106">Call the <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.FileSecurity> object that contains the current ACL entries of a file.</span></span>  
  
2. <span data-ttu-id="3304d-107">Adım 1'den döndürülen <xref:System.Security.AccessControl.FileSecurity> nesneden ACL girişleri ekleme veya kaldırma.</span><span class="sxs-lookup"><span data-stu-id="3304d-107">Add or remove ACL entries from the <xref:System.Security.AccessControl.FileSecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="3304d-108">Değişiklikleri uygulamak için nesneyi yönteme geçirin. <xref:System.Security.AccessControl.FileSecurity> <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3304d-108">To apply the changes, pass the <xref:System.Security.AccessControl.FileSecurity> object to the <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a><span data-ttu-id="3304d-109">Bir ACL girişini dizinden ekleme veya kaldırma</span><span class="sxs-lookup"><span data-stu-id="3304d-109">Add or remove an ACL entry from a directory</span></span>  
  
1. <span data-ttu-id="3304d-110">Dizinin <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> geçerli ACL <xref:System.Security.AccessControl.DirectorySecurity> girişlerini içeren bir nesneyi almak için yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="3304d-110">Call the <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.DirectorySecurity> object that contains the current ACL entries of a directory.</span></span>  
  
2. <span data-ttu-id="3304d-111">Adım 1'den döndürülen <xref:System.Security.AccessControl.DirectorySecurity> nesneden ACL girişleri ekleme veya kaldırma.</span><span class="sxs-lookup"><span data-stu-id="3304d-111">Add or remove ACL entries from the <xref:System.Security.AccessControl.DirectorySecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="3304d-112">Değişiklikleri uygulamak için nesneyi yönteme geçirin. <xref:System.Security.AccessControl.DirectorySecurity> <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3304d-112">To apply the changes, pass the <xref:System.Security.AccessControl.DirectorySecurity> object to the <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3304d-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="3304d-113">Example</span></span>  
 <span data-ttu-id="3304d-114">Bu örneği çalıştırmak için geçerli bir kullanıcı veya grup hesabı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3304d-114">You must use a valid user or group account to run this example.</span></span> <span data-ttu-id="3304d-115">Örnekbir <xref:System.IO.File> nesne kullanır.</span><span class="sxs-lookup"><span data-stu-id="3304d-115">The example uses a <xref:System.IO.File> object.</span></span> <span data-ttu-id="3304d-116"><xref:System.IO.FileInfo>Sınıflar <xref:System.IO.Directory>ve <xref:System.IO.DirectoryInfo> sınıflar için de aynı yordamı kullanın.</span><span class="sxs-lookup"><span data-stu-id="3304d-116">Use the same procedure for the <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, and <xref:System.IO.DirectoryInfo> classes.</span></span>

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
