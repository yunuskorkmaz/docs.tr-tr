---
title: 'Nasıl yapılır: Ekleme veya kaldırma erişim denetimi listesi girdileri (yalnızca .NET Framework)'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 351d8325cc0fc1a1b551b6d513cad02f1291daab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772953"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a><span data-ttu-id="5e2a9-102">Nasıl yapılır: Ekleme veya kaldırma erişim denetimi listesi girdileri (yalnızca .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="5e2a9-102">How to: Add or remove Access Control List entries (.NET Framework only)</span></span>
<span data-ttu-id="5e2a9-103">Erişim denetimi listesi (ACL) girişleri için veya bir dosya veya dizinden ekleyip için alın <xref:System.Security.AccessControl.FileSecurity> veya <xref:System.Security.AccessControl.DirectorySecurity> dosya veya dizinden nesne.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-103">To add or remove Access Control List (ACL) entries to or from a file or directory, get the <xref:System.Security.AccessControl.FileSecurity> or <xref:System.Security.AccessControl.DirectorySecurity> object from the file or directory.</span></span> <span data-ttu-id="5e2a9-104">Nesneyi değiştirmek ve dosya veya dizin için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-104">Modify the object, and then apply it back to the file or directory.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a><span data-ttu-id="5e2a9-105">Bir ACL girişi dosyadan ekleyip</span><span class="sxs-lookup"><span data-stu-id="5e2a9-105">Add or remove an ACL entry from a file</span></span>  
  
1. <span data-ttu-id="5e2a9-106">Çağrı <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> almak için yöntemi bir <xref:System.Security.AccessControl.FileSecurity> dosyasının geçerli ACL girişleri içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-106">Call the <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.FileSecurity> object that contains the current ACL entries of a file.</span></span>  
  
2. <span data-ttu-id="5e2a9-107">ACL girişleri ekleyip <xref:System.Security.AccessControl.FileSecurity> adım 1'den Nesne döndürdü.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-107">Add or remove ACL entries from the <xref:System.Security.AccessControl.FileSecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="5e2a9-108">Değişiklikleri uygulamak için geçirmek <xref:System.Security.AccessControl.FileSecurity> nesnesini <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-108">To apply the changes, pass the <xref:System.Security.AccessControl.FileSecurity> object to the <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a><span data-ttu-id="5e2a9-109">Bir ACL girişi bir dizinden ekleyip</span><span class="sxs-lookup"><span data-stu-id="5e2a9-109">Add or remove an ACL entry from a directory</span></span>  
  
1. <span data-ttu-id="5e2a9-110">Çağrı <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> almak için yöntemi bir <xref:System.Security.AccessControl.DirectorySecurity> ait geçerli bir dizin ACL girişleri içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-110">Call the <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> method to get a <xref:System.Security.AccessControl.DirectorySecurity> object that contains the current ACL entries of a directory.</span></span>  
  
2. <span data-ttu-id="5e2a9-111">ACL girişleri ekleyip <xref:System.Security.AccessControl.DirectorySecurity> adım 1'den Nesne döndürdü.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-111">Add or remove ACL entries from the <xref:System.Security.AccessControl.DirectorySecurity> object returned from step 1.</span></span>  
  
3. <span data-ttu-id="5e2a9-112">Değişiklikleri uygulamak için geçirmek <xref:System.Security.AccessControl.DirectorySecurity> nesnesini <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-112">To apply the changes, pass the <xref:System.Security.AccessControl.DirectorySecurity> object to the <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e2a9-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e2a9-113">Example</span></span>  
 <span data-ttu-id="5e2a9-114">Bu örneği çalıştırmak için geçerli bir kullanıcı veya grup hesabı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-114">You must use a valid user or group account to run this example.</span></span> <span data-ttu-id="5e2a9-115">Örnekte bir <xref:System.IO.File> nesne.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-115">The example uses a <xref:System.IO.File> object.</span></span> <span data-ttu-id="5e2a9-116">İçin aynı yordamı <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, ve <xref:System.IO.DirectoryInfo> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-116">Use the same procedure for the <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, and <xref:System.IO.DirectoryInfo> classes.</span></span>

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
