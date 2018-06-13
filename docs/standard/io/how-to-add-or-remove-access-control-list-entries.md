---
title: 'Nasıl yapılır: Erişim Denetimi Listesi Girdileri Ekleme veya Kaldırma'
ms.date: 03/30/2017
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
ms.openlocfilehash: 24c428a80f18b35d0aa3119a3c5fa1a6dcb2130e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573429"
---
# <a name="how-to-add-or-remove-access-control-list-entries"></a>Nasıl yapılır: Erişim Denetimi Listesi Girdileri Ekleme veya Kaldırma
Eklemek veya kaldırmak için veya bir dosya erişim denetimi listesi (ACL) girişleri için <xref:System.Security.AccessControl.FileSecurity> veya <xref:System.Security.AccessControl.DirectorySecurity> nesne gerekir dosya veya dizin elde, değiştirilecek ve dosya veya dizin için uygulanır.  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-file"></a>Eklemek veya bir dosyadan bir ACL girişi kaldırmak için  
  
1.  Çağrı <xref:System.IO.File.GetAccessControl%2A> almak için yöntemi bir <xref:System.Security.AccessControl.FileSecurity> dosyasının geçerli ACL girişleri içeren nesne.  
  
2.  ACL girişleri ekleyip <xref:System.Security.AccessControl.FileSecurity> nesne adım 1'den döndürdü.  
  
3.  Geçirmek <xref:System.Security.AccessControl.FileSecurity> nesnesine <xref:System.IO.File.SetAccessControl%2A> değişiklikleri uygulamak için yöntem.  
  
### <a name="to-add-or-remove-an-acl-entry-from-a-directory"></a>Eklemek veya bir dizinden bir ACL girişi kaldırmak için  
  
1.  Çağrı <xref:System.IO.Directory.GetAccessControl%2A> almak için yöntemi bir <xref:System.Security.AccessControl.DirectorySecurity> ait geçerli bir dizin ACL girişleri içeren nesne.  
  
2.  ACL girişleri ekleyip <xref:System.Security.AccessControl.DirectorySecurity> nesne adım 1'den döndürdü.  
  
3.  Geçirmek <xref:System.Security.AccessControl.DirectorySecurity> nesnesine <xref:System.IO.Directory.SetAccessControl%2A> değişiklikleri uygulamak için yöntem.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/cpp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/cpp/sample.cpp#1)]
 [!code-csharp[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/CS/sample.cs#1)]
 [!code-vb[IO.File.GetAccessControl-SetAccessControl#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.File.GetAccessControl-SetAccessControl/VB/sample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örneği çalıştırmak için geçerli bir kullanıcı veya grup hesabı girmeniz gerekir. Bu örnekte bir <xref:System.IO.File> ; ancak, aynı yordamı için kullanılan nesne <xref:System.IO.FileInfo>, <xref:System.IO.Directory>, ve <xref:System.IO.DirectoryInfo> sınıfları.
