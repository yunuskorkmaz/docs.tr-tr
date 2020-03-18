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
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a>Nasıl yapılır: Erişim Denetim Listesi girişleri ekleme veya kaldırma (yalnızca.NET Framework)
Bir dosyaya veya dizine Erişim Denetim Listesi (ACL) girişlerini <xref:System.Security.AccessControl.FileSecurity> <xref:System.Security.AccessControl.DirectorySecurity> eklemek veya kaldırmak için, dosyadan veya dizinden veya nesneden veya dosyadan nesne alın. Nesneyi değiştirin ve dosyaya veya dizine geri uygulayın.  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a>Bir Dosyadan ACL girişi ekleme veya kaldırma  
  
1. Bir <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> dosyanın geçerli <xref:System.Security.AccessControl.FileSecurity> ACL girişlerini içeren bir nesneyi almak için yöntemi arayın.  
  
2. Adım 1'den döndürülen <xref:System.Security.AccessControl.FileSecurity> nesneden ACL girişleri ekleme veya kaldırma.  
  
3. Değişiklikleri uygulamak için nesneyi yönteme geçirin. <xref:System.Security.AccessControl.FileSecurity> <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType>  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a>Bir ACL girişini dizinden ekleme veya kaldırma  
  
1. Dizinin <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> geçerli ACL <xref:System.Security.AccessControl.DirectorySecurity> girişlerini içeren bir nesneyi almak için yöntemi çağırın.  
  
2. Adım 1'den döndürülen <xref:System.Security.AccessControl.DirectorySecurity> nesneden ACL girişleri ekleme veya kaldırma.  
  
3. Değişiklikleri uygulamak için nesneyi yönteme geçirin. <xref:System.Security.AccessControl.DirectorySecurity> <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType>  
  
## <a name="example"></a>Örnek  
 Bu örneği çalıştırmak için geçerli bir kullanıcı veya grup hesabı kullanmanız gerekir. Örnekbir <xref:System.IO.File> nesne kullanır. <xref:System.IO.FileInfo>Sınıflar <xref:System.IO.Directory>ve <xref:System.IO.DirectoryInfo> sınıflar için de aynı yordamı kullanın.

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
