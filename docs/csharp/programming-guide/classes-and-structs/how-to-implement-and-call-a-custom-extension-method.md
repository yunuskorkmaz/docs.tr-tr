---
title: Özel bir genişletme yöntemi uygulama ve çağırma-C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: f9937c4b7c6e66af0ee3bc6f6d9ef3b3b1edd530
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241831"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a>Özel bir genişletme yöntemi uygulama ve çağırma (C# Programlama Kılavuzu)
Bu konu başlığı altında, tüm .NET türleri için kendi genişletme yöntemlerinizi nasıl uygulanacağı gösterilmektedir. İstemci kodu, uzantıları içeren DLL 'ye bir başvuru ekleyerek ve uzantı yöntemlerinin tanımlandığı ad alanını belirten bir [using](../../language-reference/keywords/using-directive.md) yönergesi ekleyerek uzantı yöntemlerinizi kullanabilir.  
  
## <a name="to-define-and-call-the-extension-method"></a>Genişletme yöntemini tanımlamak ve çağırmak için  
  
1. Uzantı yöntemini içerecek bir statik [sınıf](./static-classes-and-static-class-members.md) tanımlayın.  
  
     Sınıf, istemci koduna görünür olmalıdır. Erişilebilirlik kuralları hakkında daha fazla bilgi için bkz. [erişim değiştiricileri](./access-modifiers.md).  
  
2. Genişletme yöntemini, en az içeren sınıfla aynı görünürlüğe sahip statik bir yöntem olarak uygulayın.  
  
3. Metodun ilk parametresi, yöntemin üzerinde çalıştığı türü belirtir; önünde [Bu](../../language-reference/keywords/this.md) değiştiriciye sahip olmalıdır.  
  
4. Çağıran kodda, `using` uzantı yöntemi sınıfını içeren [ad alanını](../../language-reference/keywords/namespace.md) belirtmek için bir yönerge ekleyin.  
  
5. Yöntemleri, tür üzerinde örnek yöntemmiş gibi çağırın.  
  
     İlk parametrenin, işlecin uygulandığı türü temsil ettiğinden ve derleyicinin zaten nesnenizin türünü bildiği için kodu çağırarak belirtildiğine unutmayın. Yalnızca 2 ile parametreler için bağımsız değişkenler sağlamanız gerekir `n` .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sınıfında adlı bir genişletme yöntemi uygular `WordCount` `CustomExtensions.StringExtension` . Yöntemi, <xref:System.String> ilk yöntem parametresi olarak belirtilen sınıfında çalışır. `CustomExtensions`Ad alanı uygulama ad alanına aktarılır ve yöntemi yöntemi içinde çağırılır `Main` .  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-security"></a>.NET güvenliği  
 Uzantı yöntemleri, belirli bir güvenlik güvenlik açığı sunmaz. Tüm ad çakışmaları, türün kendisi tarafından tanımlanan örnek veya statik yöntem üzerinde çözümlendikleri için, bir tür üzerindeki mevcut yöntemlerin kimliğine bürünmek için hiçbir şekilde kullanılamaz. Genişletme metotları genişletilmiş sınıftaki herhangi bir özel veriye erişemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Uzantı Metotları](./extension-methods.md)
- [LINQ (dil ile tümleşik sorgu)](../../linq/linq-in-csharp.md)
- [Statik Sınıflar ve Statik Sınıf Üyeleri](./static-classes-and-static-class-members.md)
- [protected](../../language-reference/keywords/protected.md)
- [internal](../../language-reference/keywords/internal.md)
- [public](../../language-reference/keywords/public.md)
- [this](../../language-reference/keywords/this.md)
- [uzayına](../../language-reference/keywords/namespace.md)
