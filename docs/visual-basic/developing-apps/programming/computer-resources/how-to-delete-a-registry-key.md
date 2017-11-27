---
title: "Nasıl Yapılır: Visual Basic'te Kayıt Defteri Anahtarını Silme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.DeleteSetting
helpviewer_keywords:
- GetSetting function [Visual Basic]
- registry [Visual Basic], deleting values
- GetAllSettings function
- registry keys [Visual Basic], deleting
- registry [Visual Basic], deleting keys
- examples [Visual Basic], registry
ms.assetid: ab9aca0e-42b0-4ff7-8ff9-845a4bfdf9f2
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0cb98c02531bac133b9dc37a92f75d5c0418dc7c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a><span data-ttu-id="be295-102">Nasıl Yapılır: Visual Basic'te Kayıt Defteri Anahtarını Silme</span><span class="sxs-lookup"><span data-stu-id="be295-102">How to: Delete a Registry Key in Visual Basic</span></span>
<span data-ttu-id="be295-103"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> Ve <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> yöntemleri, kayıt defteri anahtarlarını silmeniz için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="be295-103">The <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> and <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> methods can be used to delete registry keys.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="be295-104">Yordam</span><span class="sxs-lookup"><span data-stu-id="be295-104">Procedure</span></span>  
  
#### <a name="to-delete-a-registry-key"></a><span data-ttu-id="be295-105">Bir kayıt defteri anahtarını silmek için</span><span class="sxs-lookup"><span data-stu-id="be295-105">To delete a registry key</span></span>  
  
-   <span data-ttu-id="be295-106">Kullanım `DeleteSubKey` yöntemi bir kayıt defteri anahtarını silin.</span><span class="sxs-lookup"><span data-stu-id="be295-106">Use the `DeleteSubKey` method to delete a registry key.</span></span> <span data-ttu-id="be295-107">Bu örnek, yazılım/TestApp Currentuser'a kovanında anahtarı siler.</span><span class="sxs-lookup"><span data-stu-id="be295-107">This example deletes the key Software/TestApp in the CurrentUser hive.</span></span> <span data-ttu-id="be295-108">Bu uygun dizeye kodda değişiklik ya da sahip kullanıcı tarafından sağlanan bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="be295-108">You can change this in the code to the appropriate string, or have it rely on user-supplied information.</span></span>  
  
     [!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-delete-a-registry-key_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="be295-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="be295-109">Robust Programming</span></span>  
 <span data-ttu-id="be295-110">`DeleteSubKey` Anahtar/değer çifti yoksa, yöntem boş bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="be295-110">The `DeleteSubKey` method returns an empty string if the key/value pair does not exist.</span></span>  
  
 <span data-ttu-id="be295-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="be295-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="be295-112">Anahtar adı `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="be295-112">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="be295-113">Kullanıcının kayıt defteri anahtarları silme izni yok (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="be295-113">The user does not have permissions to delete registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="be295-114">Anahtar adı 255 karakter sınırını aşıyor (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="be295-114">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="be295-115">Kayıt defteri anahtarı salt okunurdur (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="be295-115">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="be295-116">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="be295-116">.NET Framework Security</span></span>  
 <span data-ttu-id="be295-117">Kayıt defteri Çağrılar başarısız olur ya da yeterli çalıştırma izinleri olmayan verilirse (<xref:System.Security.Permissions.RegistryPermission>) veya kullanıcının ayarlarına oluşturulması veya doğru erişim (ACL'ler tarafından belirlendiği şekilde) yok.</span><span class="sxs-lookup"><span data-stu-id="be295-117">Registry calls fail if either sufficient run-time permissions are not granted (<xref:System.Security.Permissions.RegistryPermission>) or if the user does not have the correct access (as determined by the ACLs) for creating or writing to settings.</span></span> <span data-ttu-id="be295-118">Örneğin, kod erişimi güvenlik izni olan yerel bir uygulama işletim sistemi izni olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="be295-118">For example, a local application that has the code access security permission might not have operating system permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be295-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="be295-119">See Also</span></span>  
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>  
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>  
 <xref:Microsoft.Win32.RegistryKey>  
 [<span data-ttu-id="be295-120">Güvenlik ve kayıt defteri</span><span class="sxs-lookup"><span data-stu-id="be295-120">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 [<span data-ttu-id="be295-121">Okuma ve kayıt defterine yazma</span><span class="sxs-lookup"><span data-stu-id="be295-121">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
