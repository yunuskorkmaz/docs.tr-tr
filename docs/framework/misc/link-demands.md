---
title: Bağlantı Talepleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], demands
- demanded permissions
- permissions [.NET Framework], demands
- granting permissions, demands
- code access security, demands
- user demands for permission
- caller security checks
- link demands
ms.assetid: a33fd5f9-2de9-4653-a4f0-d9df25082c4d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2ba3172b1a82c0a9f624a49eb63a193dd29faac1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750739"
---
# <a name="link-demands"></a>Bağlantı Talepleri
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Bağlantı talebi, tam zamanında derleme sırasında güvenlik denetimi neden olur ve kodunuzun yalnızca anında çağıran derlemeye denetler. Kodunuzu işlev işaretçi başvuruları ve yöntem çağrıları dahil olmak üzere, bir tür başvurusu ile ilişkili bağlama gerçekleşir. Çağrıyı yapan derlemeyi, koda bağlamak için yeterli izne sahip değilse bağlantıya izin verilmiyor ve bir çalışma zamanı özel durum kodu yüklendi ve çalıştırın. Bağlantı talepleri kodunuzdan devralınan sınıflardaki geçersiz kılınabilir.  
  
 Bu talep türü ile tam bir yığın ilerlemesi yapılmaz ve kodunuzu saldırıları luring için saldırılara açıktır unutmayın. Derlemesi içindeki bir yöntemi bağlantı talebi tarafından korunuyorsa, örneğin, derleme B içinde doğrudan çağıran derleme B'nin izinlere göre değerlendirilir  Yöntemini kullanarak b derlemede derlemesindeki dolaylı olarak yöntemini çağırır, ancak bağlantı talebi C derlemesindeki bir yöntemi işlemeyecek Bağlantı talebi, koda bağlamak çağıranlar, hemen çağıran derlemeye olmalıdır yalnızca izinleri doğrudan belirtir. Tüm çağıranların kodunuzu çalıştırmak için sahip olmanız gereken izinleri belirtmiyor.  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, Ve <xref:System.Security.CodeAccessPermission.PermitOnly%2A> yığın ilerlemesi değiştiriciler bağlantı talepleri değerlendirmesi etkilemez.  Bağlantı talepleri yığın ilerlemesi gerçekleştirmediği için yığın ilerlemesi değiştiriciler bağlantı talepleri üzerinde etkisi yoktur.  
  
 Bağlantı talebi tarafından korunan bir yöntem aracılığıyla erişilen, [yansıma](../../../docs/framework/reflection-and-codedom/reflection.md), sonra da bağlantı talebi yansıma yoluyla erişilen kod şu anki çağırıcı denetler. Bu, hem yöntemi bulma ve yansıma kullanılarak gerçekleştirilen yöntem çağırma için geçerlidir. Örneğin, kod döndürmek için yansıtma kullanır varsayalım. bir <xref:System.Reflection.MethodInfo> bağlantı talebi tarafından korunan ve ardından geçiren bir yöntemi temsil eden nesne **MethodInfo** nesnenin orijinal yöntemini çağırmak için kullandığı bazı bir kod için nesne. Bu durumda bağlantı talebi onay iki kez oluşuyor: döndüren kod için bir kez **MethodInfo** nesne ve onu çağıran kod için bir kez.  
  
> [!NOTE]
>  Statik oluşturucular dışında uygulamanın kod yürütme yolu sistem tarafından çağrıldığı bir statik sınıf oluşturucu üzerinde gerçekleştirilen bağlantı talebi Oluşturucu korumaz. Bağlantı talebi tamamını bir sınıfa uygulandığında, sınıfın rest korumak ancak sonuç olarak, bu erişim için bir statik Oluşturucu koruyamaz.  
  
 Aşağıdaki kod parçası, bildirimli herhangi kod bağlama belirtir `ReadData` yöntemi olmalıdır `CustomPermission` izni. Bu izin, kuramsal bir özel izni ve .NET Framework'teki yok. İsteğe bağlı geçirerek yapılan bir **SecurityAction.LinkDemand** bayrak `CustomPermissionAttribute`.  
  
```vb  
<CustomPermissionAttribute(SecurityAction.LinkDemand)> _  
Public Shared Function ReadData() As String  
    ' Access a custom resource.  
End Function    
```  
  
```csharp  
[CustomPermissionAttribute(SecurityAction.LinkDemand)]  
public static string ReadData()  
{  
    // Access a custom resource.  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öznitelikler](../../../docs/standard/attributes/index.md)
- [Kod erişimi güvenliği](../../../docs/framework/misc/code-access-security.md)
