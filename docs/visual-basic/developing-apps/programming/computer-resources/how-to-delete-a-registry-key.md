---
title: 'Nasıl Yapılır: Kayıt Defteri Anahtarını Silme'
ms.date: 07/20/2015
f1_keywords:
- vb.DeleteSetting
helpviewer_keywords:
- GetSetting function [Visual Basic]
- registry [Visual Basic], deleting values
- GetAllSettings function
- registry keys [Visual Basic], deleting
- registry [Visual Basic], deleting keys
- examples [Visual Basic], registry
ms.assetid: ab9aca0e-42b0-4ff7-8ff9-845a4bfdf9f2
ms.openlocfilehash: f38301a3a717a35b98e55804d6435d046bbbbab4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345647"
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a><span data-ttu-id="c7db2-102">Nasıl Yapılır: Visual Basic'te Kayıt Defteri Anahtarını Silme</span><span class="sxs-lookup"><span data-stu-id="c7db2-102">How to: Delete a Registry Key in Visual Basic</span></span>

<span data-ttu-id="c7db2-103"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> ve <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> yöntemleri kayıt defteri anahtarlarını silmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c7db2-103">The <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> and <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> methods can be used to delete registry keys.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="c7db2-104">Yordam</span><span class="sxs-lookup"><span data-stu-id="c7db2-104">Procedure</span></span>  
  
#### <a name="to-delete-a-registry-key"></a><span data-ttu-id="c7db2-105">Kayıt defteri anahtarını silmek için</span><span class="sxs-lookup"><span data-stu-id="c7db2-105">To delete a registry key</span></span>  
  
- <span data-ttu-id="c7db2-106">Bir kayıt defteri anahtarını silmek için `DeleteSubKey` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7db2-106">Use the `DeleteSubKey` method to delete a registry key.</span></span> <span data-ttu-id="c7db2-107">Bu örnek, geçerli kullanıcı kovanındaki Key Software/TestApp öğesini siler.</span><span class="sxs-lookup"><span data-stu-id="c7db2-107">This example deletes the key Software/TestApp in the CurrentUser hive.</span></span> <span data-ttu-id="c7db2-108">Bu kodu kodda uygun dizeye değiştirebilir veya Kullanıcı tarafından sağlanan bilgileri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="c7db2-108">You can change this in the code to the appropriate string, or have it rely on user-supplied information.</span></span>  
  
     [!code-vb[VbResourceTasks#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a><span data-ttu-id="c7db2-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="c7db2-109">Robust Programming</span></span>  

 <span data-ttu-id="c7db2-110">Anahtar/değer çifti yoksa `DeleteSubKey` yöntemi boş bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="c7db2-110">The `DeleteSubKey` method returns an empty string if the key/value pair does not exist.</span></span>  
  
 <span data-ttu-id="c7db2-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="c7db2-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="c7db2-112">Anahtarın adı `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="c7db2-112">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="c7db2-113">Kullanıcının kayıt defteri anahtarlarını silme izni yok (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="c7db2-113">The user does not have permissions to delete registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="c7db2-114">Anahtar adı 255 karakterlik sınırı (<xref:System.ArgumentException>) aşıyor.</span><span class="sxs-lookup"><span data-stu-id="c7db2-114">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="c7db2-115">Kayıt defteri anahtarı salt okunurdur (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="c7db2-115">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c7db2-116">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c7db2-116">.NET Framework Security</span></span>  

 <span data-ttu-id="c7db2-117">Yeterli çalışma zamanı izni verilmezse (<xref:System.Security.Permissions.RegistryPermission>) veya Kullanıcı, ayarları oluşturmaya veya bu ayarlara yazmaya yönelik doğru erişime (ACL 'Ler tarafından belirlendiği şekilde) sahip değilse, kayıt defteri çağrıları başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="c7db2-117">Registry calls fail if either sufficient run-time permissions are not granted (<xref:System.Security.Permissions.RegistryPermission>) or if the user does not have the correct access (as determined by the ACLs) for creating or writing to settings.</span></span> <span data-ttu-id="c7db2-118">Örneğin, kod erişim güvenliği iznine sahip bir yerel uygulama işletim sistemi iznine sahip olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="c7db2-118">For example, a local application that has the code access security permission might not have operating system permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7db2-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7db2-119">See also</span></span>

- <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>
- <xref:Microsoft.Win32.RegistryKey>
- [<span data-ttu-id="c7db2-120">Güvenlik ve Kayıt Defteri</span><span class="sxs-lookup"><span data-stu-id="c7db2-120">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
- [<span data-ttu-id="c7db2-121">Kayıt Defterinden Okuma ve Kayıt Defterine Yazma</span><span class="sxs-lookup"><span data-stu-id="c7db2-121">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
