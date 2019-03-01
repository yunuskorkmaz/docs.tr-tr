---
title: "Nasıl yapılır: Visual Basic'te kayıt defteri anahtarını silme"
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
ms.openlocfilehash: 7ff6ba8e31638b64fa7100b1807303c61a454c81
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981679"
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a><span data-ttu-id="d06fe-102">Nasıl yapılır: Visual Basic'te kayıt defteri anahtarını silme</span><span class="sxs-lookup"><span data-stu-id="d06fe-102">How to: Delete a Registry Key in Visual Basic</span></span>
<span data-ttu-id="d06fe-103"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> Ve <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> yöntemleri, kayıt defteri anahtarlarını silmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d06fe-103">The <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> and <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> methods can be used to delete registry keys.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="d06fe-104">Yordam</span><span class="sxs-lookup"><span data-stu-id="d06fe-104">Procedure</span></span>  
  
#### <a name="to-delete-a-registry-key"></a><span data-ttu-id="d06fe-105">Bir kayıt defteri anahtarını silin</span><span class="sxs-lookup"><span data-stu-id="d06fe-105">To delete a registry key</span></span>  
  
-   <span data-ttu-id="d06fe-106">Kullanım `DeleteSubKey` yöntemi bir kayıt defteri anahtarını silin.</span><span class="sxs-lookup"><span data-stu-id="d06fe-106">Use the `DeleteSubKey` method to delete a registry key.</span></span> <span data-ttu-id="d06fe-107">Bu örnek, ' % s'anahtarı yazılım/TestApp CurrentUser kovanında siler.</span><span class="sxs-lookup"><span data-stu-id="d06fe-107">This example deletes the key Software/TestApp in the CurrentUser hive.</span></span> <span data-ttu-id="d06fe-108">Bu, uygun dize olan kodda değişiklik veya bu kullanıcı tarafından sağlanan bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="d06fe-108">You can change this in the code to the appropriate string, or have it rely on user-supplied information.</span></span>  
  
     [!code-vb[VbResourceTasks#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d06fe-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="d06fe-109">Robust Programming</span></span>  
 <span data-ttu-id="d06fe-110">`DeleteSubKey` Yöntem, anahtar/değer çifti mevcut değilse boş bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="d06fe-110">The `DeleteSubKey` method returns an empty string if the key/value pair does not exist.</span></span>  
  
 <span data-ttu-id="d06fe-111">Aşağıdaki koşullar özel bir duruma neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="d06fe-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="d06fe-112">Anahtar adı `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="d06fe-112">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="d06fe-113">Kullanıcının kayıt defteri anahtarları silme izni yok (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="d06fe-113">The user does not have permissions to delete registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="d06fe-114">Anahtar adı 255 karakter sınırını aşıyor (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="d06fe-114">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="d06fe-115">Kayıt defteri anahtarı salt okunurdur (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="d06fe-115">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d06fe-116">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="d06fe-116">.NET Framework Security</span></span>  
 <span data-ttu-id="d06fe-117">Kayıt defteri çağrıları başarısız yeterli ya da çalışma zamanı izinler verilmezse (<xref:System.Security.Permissions.RegistryPermission>) veya kullanıcı oluşturma veya ayarlarına yazma için doğru erişim (ACL'ler tarafından belirlendiği şekilde) sahip değil.</span><span class="sxs-lookup"><span data-stu-id="d06fe-117">Registry calls fail if either sufficient run-time permissions are not granted (<xref:System.Security.Permissions.RegistryPermission>) or if the user does not have the correct access (as determined by the ACLs) for creating or writing to settings.</span></span> <span data-ttu-id="d06fe-118">Örneğin, kod erişim güvenlik izni olan yerel bir uygulama işletim sistemi izniniz olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="d06fe-118">For example, a local application that has the code access security permission might not have operating system permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d06fe-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d06fe-119">See also</span></span>
- <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>
- <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>
- <xref:Microsoft.Win32.RegistryKey>
- [<span data-ttu-id="d06fe-120">Güvenlik ve Kayıt Defteri</span><span class="sxs-lookup"><span data-stu-id="d06fe-120">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
- [<span data-ttu-id="d06fe-121">Kayıt Defterinden Okuma ve Kayıt Defterine Yazma</span><span class="sxs-lookup"><span data-stu-id="d06fe-121">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
