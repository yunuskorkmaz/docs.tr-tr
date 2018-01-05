---
title: "Nasıl yapılır: Erişim Denetimi Listesi Girdileri Ekleme veya Kaldırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 988fd354caa5fcc716107087242ead113c9a9939
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-add-or-remove-access-control-list-entries"></a><span data-ttu-id="7bcd7-102">Nasıl yapılır: Erişim Denetimi Listesi Girdileri Ekleme veya Kaldırma</span><span class="sxs-lookup"><span data-stu-id="7bcd7-102">How to: Add or Remove Access Control List Entries</span></span>
<span data-ttu-id="7bcd7-103">Eklemek veya kaldırmak için veya bir dosya erişim denetimi listesi (ACL) girişleri için <xref:System.Security.AccessControl.FileSecurity> veya <xref:System.Security.AccessControl.DirectorySecurity> nesne gerekir dosya veya dizin elde, değiştirilecek ve dosya veya dizin için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7bcd7-103">To add or remove Access Control List (ACL) entries to or from a file, the <xref:System.Security.AccessControl.FileSecurity> or <xref:System.Security.AccessControl.DirectorySecurity> object must be obtained from the file or directory, modified, and then applied back to the file or directory.</span></span>  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-file"></a><span data-ttu-id="7bcd7-104">Eklemek veya bir dosyadan bir ACL girişi kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="7bcd7-104">To add or remove an ACL entry from a File</span></span>  
  
1.  <span data-ttu-id="7bcd7-105">Çağrı <xref:System.IO.File.GetAccessControl%2A> almak için yöntemi bir <xref:System.Security.AccessControl.FileSecurity> dosyasının geçerli ACL girişleri içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="7bcd7-105">Call the <xref:System.IO.File.GetAccessControl%2A> method to get a <xref:System.Security.AccessControl.FileSecurity> object that contains the current ACL entries of a file.</span></span>  
  
2.  <span data-ttu-id="7bcd7-106">ACL girişleri ekleyip <xref:System.Security.AccessControl.FileSecurity> nesne adım 1'den döndürdü.</span><span class="sxs-lookup"><span data-stu-id="7bcd7-106">Add or remove ACL entries from the <xref:System.Security.AccessControl.FileSecurity> object returned from step 1.</span></span>  
  
3.  <span data-ttu-id="7bcd7-107">Geçirmek <xref:System.Security.AccessControl.FileSecurity> nesnesine <xref:System.IO.File.SetAccessControl%2A> değişiklikleri uygulamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="7bcd7-107">Pass the <xref:System.Security.AccessControl.FileSecurity> object to the <xref:System.IO.File.SetAccessControl%2A> method to apply the changes.</span></span>  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-directory"></a><span data-ttu-id="7bcd7-108">Eklemek veya bir dizinden bir ACL girişi kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="7bcd7-108">To add or remove an ACL entry from a Directory</span></span>  
  
1.  <span data-ttu-id="7bcd7-109">Çağrı <xref:System.IO.Directory.GetAccessControl%2A> almak için yöntemi bir <xref:System.Security.AccessControl.DirectorySecurity> ait geçerli bir dizin ACL girişleri içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="7bcd7-109">Call the <xref:System.IO.Directory.GetAccessControl%2A> method to get a <xref:System.Security.AccessControl.DirectorySecurity> object that contains the current ACL entries of a directory.</span></span>  
  
2.  <span data-ttu-id="7bcd7-110">ACL girişleri ekleyip <xref:System.Security.AccessControl.DirectorySecurity> nesne adım 1'den döndürdü.</span><span class="sxs-lookup"><span data-stu-id="7bcd7-110">Add or remove ACL entries from the <xref:System.Security.AccessControl.DirectorySecurity> object returned from step 1.</span></span>  
  
3.  <span data-ttu-id="7bcd7-111">Geçirmek <xref:System.Security.AccessControl.DirectorySecurity> nesnesine <xref:System.IO.Directory.SetAccessControl%2A> değişiklikleri uygulamak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="7bcd7-111">Pass the <xref:System.Security.AccessControl.DirectorySecurity> object to the <xref:System.IO.Directory.SetAccessControl%2A> method to apply the changes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bcd7-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="7bcd7-112">Example</span></span>  
 [!code-cpp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/cpp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/cpp/sample.cpp#1)]
 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7bcd7-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="7bcd7-113">Compiling the Code</span></span>  
 <span data-ttu-id="7bcd7-114">Bu örneği çalıştırmak için geçerli bir kullanıcı veya grup hesabı girmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7bcd7-114">You must supply a valid user or group account to run this example.</span></span> <span data-ttu-id="7bcd7-115">Bu örnekte bir <xref:System.IO.File> ; ancak, aynı yordamı için kullanılan nesne <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, ve <xref:System.IO.DirectoryInfo> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="7bcd7-115">This example uses a <xref:System.IO.File> object; however, the same procedure is used for the <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, and <xref:System.IO.DirectoryInfo> classes.</span></span>
