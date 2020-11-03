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
ms.openlocfilehash: ff5a09207b3a1d810f9611dd6bb8cfd206adf1e8
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93187976"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a>Nasıl yapılır: Access Control listesi girdileri ekleme veya kaldırma (yalnızca .NET Framework)

Bir dosya veya dizine Access Control List (ACL) girişi eklemek veya kaldırmak için, veya dizininden dosya ya da <xref:System.Security.AccessControl.FileSecurity> <xref:System.Security.AccessControl.DirectorySecurity> Dizin alın. Nesneyi değiştirin ve ardından dosyayı veya dizini yeniden uygulayın.  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a>Dosyadan ACL girişi ekleme veya kaldırma  
  
1. <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> <xref:System.Security.AccessControl.FileSecurity> Bir DOSYANıN geçerli ACL girdilerini içeren bir nesne almak için yöntemini çağırın.  
  
2. <xref:System.Security.AccessControl.FileSecurity>1. adımdan döndürülen NESNEDEN ACL girişi ekleyin veya kaldırın.  
  
3. Değişiklikleri uygulamak için, <xref:System.Security.AccessControl.FileSecurity> nesneyi <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> yöntemine geçirin.  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a>Bir dizinden ACL girişi ekleme veya kaldırma  
  
1. <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> <xref:System.Security.AccessControl.DirectorySecurity> Bir DIZININ geçerli ACL girdilerini içeren bir nesne almak için yöntemini çağırın.  
  
2. <xref:System.Security.AccessControl.DirectorySecurity>1. adımdan döndürülen NESNEDEN ACL girişi ekleyin veya kaldırın.  
  
3. Değişiklikleri uygulamak için, <xref:System.Security.AccessControl.DirectorySecurity> nesneyi <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> yöntemine geçirin.  
  
## <a name="example"></a>Örnek  
 Bu örneği çalıştırmak için geçerli bir kullanıcı veya grup hesabı kullanmanız gerekir. Örnek bir nesnesi kullanır <xref:System.IO.File> . <xref:System.IO.FileInfo>, <xref:System.IO.Directory> , Ve sınıfları için aynı yordamı kullanın <xref:System.IO.DirectoryInfo> .

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
