---
title: Bağlantı Talepleri
description: Tam zamanında (JıT) derleme sırasında güvenlik denetimine neden olan bağlantı taleplerini okuyun ve yalnızca kodunuzun hemen çağıran derlemesini inceleyin.
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
ms.openlocfilehash: 7f5475d5bfff8cc3c500f95b05d54daacc9b253e
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855796"
---
# <a name="link-demands"></a>Bağlantı Talepleri

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Bir bağlantı isteği, tam zamanında derleme sırasında bir güvenlik denetimine neden olur ve yalnızca kodunuzun hemen çağıran derlemesini denetler. Bağlama, kodunuz işlev işaretçisi başvuruları ve Yöntem çağrıları dahil olmak üzere bir tür başvurusuna bağlandığında oluşur. Çağıran derlemenin kodunuza bağlamak için yeterli izni yoksa, bağlantıya izin verilmez ve kod yüklenip çalıştırıldığında bir çalışma zamanı özel durumu oluşturulur. Bağlantı talepleri, kodunuzun devraldığı sınıflarda geçersiz kılınabilir.  
  
 Bu talep türü ile tam bir yığın yürüme gerçekleştirilmez ve kodunuzun yine de devam eden saldırılara açıktır. Örneğin, derleme A içindeki bir yöntem bir bağlantı talebi tarafından korunuyorsa, B derlemesinde doğrudan çağıran derleme B 'nin izinlerine göre değerlendirilir.  Ancak, bağlantı isteği, derleme B içindeki yöntemi kullanarak dolaylı olarak bir derlemeyi çağıran derleme C 'deki bir yöntemi değerlendirmeyecektir. Bağlantı talebi yalnızca hemen çağıran derlemede bulunan izin doğrudan çağıranlarının kodunuza bağlanması için sahip olması gerektiğini belirtir. Tüm çağıranların kodunuzu çalıştırmak için sahip olması gereken izinleri belirtmez.  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A> Ve <xref:System.Security.CodeAccessPermission.PermitOnly%2A> Yığın ilerleme değiştiricileri bağlantı taleplerinin değerlendirilmesini etkilemez.  Bağlantı talepleri bir yığın ilerleme işlemi gerçekleştirmediğinden, yığın ilerleme değiştiricilerin bağlantı taleplerini etkilemez.  
  
 Bir bağlantı talebi tarafından korunan bir yönteme [yansıma](../reflection-and-codedom/reflection.md)aracılığıyla erişiliyorsa, bağlantı talebi, yansıma aracılığıyla erişilen kodun hemen çağırışını denetler. Bu, hem yöntem bulma hem de yansıma kullanılarak gerçekleştirilen yöntem çağırma için geçerlidir. Örneğin, kodun <xref:System.Reflection.MethodInfo> bir bağlantı talebi tarafından korunan bir yöntemi temsil eden bir nesneyi döndürmek için yansıma kullandığını varsayın ve sonra bu **MethodInfo** nesnesini, özgün yöntemi çağırmak için nesnesini kullanan başka bir koda geçirir. Bu durumda, bağlantı isteği denetimi iki kez gerçekleşir: **MethodInfo** nesnesini döndüren kod için bir kez ve onu çağıran kod için bir kez.  
  
> [!NOTE]
> Statik oluşturucular, uygulamanın kod yürütme yolu dışında, sistem tarafından çağrılamadığından, statik sınıf oluşturucusunda gerçekleştirilen bir bağlantı isteği oluşturucuyu korumaz. Sonuç olarak, bir bağlantı isteği tüm sınıfa uygulandığında, sınıfın geri kalanını korusa da statik bir oluşturucuya erişimi koruyamaz.  
  
 Aşağıdaki kod parçası bildirimli olarak, yönteme bağlanan herhangi bir kodun `ReadData` izne sahip olması gerektiğini belirtir `CustomPermission` . Bu izin kuramsal bir özel izindir ve .NET Framework yok. Talep, öğesine bir **SecurityAction. LinkDemand** bayrağı geçirilerek yapılır `CustomPermissionAttribute` .  
  
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
