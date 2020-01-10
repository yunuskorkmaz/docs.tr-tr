---
title: 'Nasıl yapılır: Access Control listesi girdileri ekleme veya kaldırma (yalnızca .NET Framework)'
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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708134"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a>Nasıl yapılır: Access Control listesi girdileri ekleme veya kaldırma (yalnızca .NET Framework)
Bir dosya veya dizine Access Control List (ACL) girişi eklemek veya kaldırmak için, <xref:System.Security.AccessControl.FileSecurity> veya <xref:System.Security.AccessControl.DirectorySecurity> nesnesini dosya veya dizinden alın. Nesneyi değiştirin ve ardından dosyayı veya dizini yeniden uygulayın.  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a>Dosyadan ACL girişi ekleme veya kaldırma  
  
1. Bir dosyanın geçerli ACL girdilerini içeren bir <xref:System.Security.AccessControl.FileSecurity> nesnesi almak için <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> yöntemini çağırın.  
  
2. 1\. adımdan döndürülen <xref:System.Security.AccessControl.FileSecurity> nesnesinden ACL girişi ekleyin veya kaldırın.  
  
3. Değişiklikleri uygulamak için <xref:System.Security.AccessControl.FileSecurity> nesnesini <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> yöntemine geçirin.  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a>Bir dizinden ACL girişi ekleme veya kaldırma  
  
1. Bir dizinin geçerli ACL girdilerini içeren bir <xref:System.Security.AccessControl.DirectorySecurity> nesnesi almak için <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> yöntemini çağırın.  
  
2. 1\. adımdan döndürülen <xref:System.Security.AccessControl.DirectorySecurity> nesnesinden ACL girişi ekleyin veya kaldırın.  
  
3. Değişiklikleri uygulamak için <xref:System.Security.AccessControl.DirectorySecurity> nesnesini <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> yöntemine geçirin.  
  
## <a name="example"></a>Örnek  
 Bu örneği çalıştırmak için geçerli bir kullanıcı veya grup hesabı kullanmanız gerekir. Örnek, <xref:System.IO.File> nesnesi kullanır. <xref:System.IO.FileInfo>, <xref:System.IO.Directory>ve <xref:System.IO.DirectoryInfo> sınıfları için aynı yordamı kullanın.

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
