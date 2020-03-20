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
ms.openlocfilehash: a0466eb5c24840c77a3b191f9b0e001f6b267fca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181169"
---
# <a name="link-demands"></a>Bağlantı Talepleri
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Bağlantı talebi, tam zamanında derleme sırasında bir güvenlik denetimine neden olur ve yalnızca kodunuzun hemen çağrı montajını denetler. Bağlama, kodunuz işlev işaretçisi başvuruları ve yöntem çağrıları da dahil olmak üzere bir tür başvurusuna bağlandığında oluşur. Arama derlemesi kodunuza bağlanmak için yeterli izine sahip değilse, bağlantıya izin verilmez ve kod yüklenip çalıştırıldığında çalışma zamanı özel durumu atılır. Bağlantı talepleri, kodunuzdan devralınan sınıflarda geçersiz kılınabilir.  
  
 Tam yığın yürüyüşü bu tür bir taleple gerçekleştirilmediğini ve kodunuzu hala çekme saldırılarına karşı duyarlı olduğunu unutmayın. Örneğin, A derlemesindeki bir yöntem bağlantı talebi yle korunuyorsa, B derlemesinde doğrudan arayan, B Derlemesi izinlerine göre değerlendirilir.  Ancak, bağlantı talebi, B derlemesindeki yöntemi kullanarak A derlemesindeki yöntemi dolaylı olarak çağırırsa, C derlemesindeki bir yöntemi değerlendirmez. Bağlantı talebi, yalnızca hemen arama derlemesindeki doğrudan arayanların kodunuza bağlanması gereken izinleri belirtir. Tüm arayanların kodunuzu çalıştırmak için çalışması gereken izinleri belirtmez.  
  
 , <xref:System.Security.CodeAccessPermission.Assert%2A> <xref:System.Security.CodeAccessPermission.Deny%2A>ve <xref:System.Security.CodeAccessPermission.PermitOnly%2A> yığın yürüyüş değiştiriciler bağlantı taleplerinin değerlendirilmesi etkilemez.  Bağlantı talepleri yığın yürüyüşü yapmadığından, yığın yürüyüş değiştiriciler bağlantı talepleri üzerinde hiçbir etkisi yoktur.  
  
 Bağlantı talebi tarafından korunan bir [yönteme Yansıma](../reflection-and-codedom/reflection.md)aracılığıyla erişilirse, bağlantı talebi yansıma aracılığıyla erişilen kodun hemen arayanını denetler. Bu, hem yöntem bulma hem de yansıma kullanılarak gerçekleştirilen yöntem çağırma için geçerlidir. Örneğin, kodun bir bağlantı <xref:System.Reflection.MethodInfo> talebi tarafından korunan bir yöntemi temsil eden bir nesneyi döndürmek için yansıma kullandığını ve sonra bu **MethodInfo** nesnesini özgün yöntemi çağırmak için nesneyi kullanan başka bir koda aktardığını varsayalım. Bu durumda bağlantı talebi denetimi iki kez oluşur: Bir kez **MethodInfo** nesnesini döndüren kod için ve bir kez de onu çağıran kod için.  
  
> [!NOTE]
> Statik yapı oluşturucuüzerinde gerçekleştirilen bir bağlantı talebi, uygulamanın kod yürütme yolu dışında, sistem tarafından çağrıldığı için yapıcıyı korumaz. Sonuç olarak, bir bağlantı talebi tüm sınıfa uygulandığında, sınıfın geri kalanını korusa da statik bir oluşturucuya erişimi koruyamaz.  
  
 Aşağıdaki kod parçası bildirimsel olarak `ReadData` yönteme bağlantı veren herhangi `CustomPermission` bir kodun izin alması gerektiğini belirtir. Bu izin varsayımsal bir özel izindir ve .NET Framework'de bulunmaz. Talep bir **SecurityAction.LinkDemand** bayrağı geçerek `CustomPermissionAttribute`yapılır.  
  
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

- [Öznitelikler](../../standard/attributes/index.md)
- [Kod Erişimi Güvenliği](code-access-security.md)
