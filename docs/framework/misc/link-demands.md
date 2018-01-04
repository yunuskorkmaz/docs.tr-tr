---
title: "Bağlantı Talepleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e59ae7b0c26106f19f5b14290047deb9b5f30c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="link-demands"></a>Bağlantı Talepleri
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Bir bağlantı isteği güvenlik denetimi tam zamanında derleme sırasında neden olur ve yalnızca hemen çağrıyı yapan derlemeyi kodunuzu denetler. Kodunuzu işlev işaretçisi başvuruları ve yöntem çağrıları dahil olmak üzere bir tür referansı bağlandığında bağlama oluşur. Çağrıyı yapan derlemeyi kodunuzu bağlamak için yeterli izni yok, bağlantıyı verilmez ve kodu yüklenen ve Çalıştır çalışma zamanı özel durum oluşur. Bağlantı talepleri kodunuzdan devralınan sınıflar geçersiz kılınabilir.  
  
 Tam yığın ilerlemesi isteğe bağlı bu tür yapılmaz ve kodunuzu saldırıları luring için hala açık olduğunu unutmayın. Derlemesi yönteminde bir bağlantı isteği tarafından korunuyorsa, örneğin, doğrudan çağıran B derlemesindeki derleme B'deki izinlerine göre değerlendirilir  Bu yöntem kullanılarak derleme B. derleme dolaylı olarak yöntemi çağırırsa ancak, bağlantı isteği C derlemesindeki yöntemi işlemeyecek Bağlantı isteği hemen çağrıyı yapan derlemeyi arayanlar kodunuzu bağlamak zorunda gerekir yalnızca izinleri doğrudan belirtir. Tüm arayanlar kodunuzu çalıştırmak için gereken izinleri belirtmiyor.  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, Ve <xref:System.Security.CodeAccessPermission.PermitOnly%2A> yığın ilerlemesi değiştiricileri bağlantı talepleri değerlendirmesi etkilemez.  Bağlantı talepleri yığın ilerlemesi gerçekleştirmediği için yığın ilerlemesi değiştiricileri bağlantı talepleri üzerinde hiçbir etkisi yoktur.  
  
 Bir bağlantı isteği tarafından korunan bir yöntem aracılığıyla erişilen varsa [yansıma](../../../docs/framework/reflection-and-codedom/reflection.md), sonra da Yansıtma üzerinden erişilen kodunun ilk çağıran bir bağlantı isteği denetler. Bu, yöntem bulma ve yansıma kullanarak gerçekleştirilen yöntem çağırma için geçerlidir. Örneğin, kod döndürülecek yansıma kullandığını varsayın bir <xref:System.Reflection.MethodInfo> nesne bir yöntemi temsil eden bir bağlantı isteği tarafından korunan ve sonra geçen **MethodInfo** nesnenin özgün yöntemini çağırmak için kullandığı bazı bir kod nesnesine. Bu durumda bağlantı isteğe bağlı onay iki kez oluşur: döndürür kodu için bir kez **MethodInfo** nesne ve onu çağıran kodu için bir kez.  
  
> [!NOTE]
>  Statik oluşturucular uygulamanın kodu yürütme yolu dışında sistem tarafından denir çünkü bir statik sınıf oluşturucu üzerinde gerçekleştirilen bir bağlantı isteği Oluşturucusu korumaz. Bir bağlantı isteği tüm bir sınıfa uygulandığında, sınıfı kalan korunmasına rağmen sonuç olarak, bu erişim statik oluşturucuya koruyamaz.  
  
 Aşağıdaki kod parçası, bildirimli olarak herhangi bir kod bağlantılandırma belirtir `ReadData` yöntemi olmalıdır `CustomPermission` izni. Bu izni kuramsal özel izinleri ve .NET Framework mevcut değil. İsteğe bağlı geçirerek yapılan bir **SecurityAction.LinkDemand** bayrağını `CustomPermissionAttribute`.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öznitelikler](../../../docs/standard/attributes/index.md)  
 [Kod erişimi güvenliği](../../../docs/framework/misc/code-access-security.md)
