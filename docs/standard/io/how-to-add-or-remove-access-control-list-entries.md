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
ms.openlocfilehash: ea1059f541d2449a1a2d5dca1644ce8d9a553e40
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283354"
---
# <a name="how-to-add-or-remove-access-control-list-entries-net-framework-only"></a>Nasıl yapılır: Ekleme veya kaldırma erişim denetimi listesi girdileri (yalnızca .NET Framework)
Erişim denetimi listesi (ACL) girişleri için veya bir dosya veya dizinden ekleyip için alın <xref:System.Security.AccessControl.FileSecurity> veya <xref:System.Security.AccessControl.DirectorySecurity> dosya veya dizinden nesne. Nesneyi değiştirmek ve dosya veya dizin için geçerlidir.  
  
## <a name="add-or-remove-an-acl-entry-from-a-file"></a>Bir ACL girişi dosyadan ekleyip  
  
1.  Çağrı <xref:System.IO.File.GetAccessControl%2A?displayProperty=nameWithType> almak için yöntemi bir <xref:System.Security.AccessControl.FileSecurity> dosyasının geçerli ACL girişleri içeren nesne.  
  
2.  ACL girişleri ekleyip <xref:System.Security.AccessControl.FileSecurity> adım 1'den Nesne döndürdü.  
  
3. Değişiklikleri uygulamak için geçirmek <xref:System.Security.AccessControl.FileSecurity> nesnesini <xref:System.IO.File.SetAccessControl%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="add-or-remove-an-acl-entry-from-a-directory"></a>Bir ACL girişi bir dizinden ekleyip  
  
1.  Çağrı <xref:System.IO.Directory.GetAccessControl%2A?displayProperty=nameWithType> almak için yöntemi bir <xref:System.Security.AccessControl.DirectorySecurity> ait geçerli bir dizin ACL girişleri içeren nesne.  
  
2.  ACL girişleri ekleyip <xref:System.Security.AccessControl.DirectorySecurity> adım 1'den Nesne döndürdü.  
  
3.  Değişiklikleri uygulamak için geçirmek <xref:System.Security.AccessControl.DirectorySecurity> nesnesini <xref:System.IO.Directory.SetAccessControl%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="example"></a>Örnek  
 Bu örneği çalıştırmak için geçerli bir kullanıcı veya grup hesabı kullanmanız gerekir. Örnekte bir <xref:System.IO.File> nesne. İçin aynı yordamı <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, ve <xref:System.IO.DirectoryInfo> sınıfları.

 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
  
