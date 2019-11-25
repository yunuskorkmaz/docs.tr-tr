---
title: Özel bir genişletme yöntemi uygulama ve çağırma- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: f3d96c033380698ade37c49ecbfeed14f05d3e11
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970888"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a>Özel bir genişletme yöntemi uygulama ve çağırma (C# Programlama Kılavuzu)
Bu konu başlığı altında, tüm .NET türleri için kendi genişletme yöntemlerinizi nasıl uygulanacağı gösterilmektedir. İstemci kodu, uzantıları içeren DLL 'ye bir başvuru ekleyerek ve uzantı yöntemlerinin tanımlandığı ad alanını belirten bir [using](../../language-reference/keywords/using-directive.md) yönergesi ekleyerek uzantı yöntemlerinizi kullanabilir.  
  
## <a name="to-define-and-call-the-extension-method"></a>Genişletme yöntemini tanımlamak ve çağırmak için  
  
1. Uzantı yöntemini içerecek bir statik [sınıf](./static-classes-and-static-class-members.md) tanımlayın.  
  
     Sınıf, istemci koduna görünür olmalıdır. Erişilebilirlik kuralları hakkında daha fazla bilgi için bkz. [erişim değiştiricileri](./access-modifiers.md).  
  
2. Genişletme yöntemini, en az içeren sınıfla aynı görünürlüğe sahip statik bir yöntem olarak uygulayın.  
  
3. Metodun ilk parametresi, yöntemin üzerinde çalıştığı türü belirtir; önünde [Bu](../../language-reference/keywords/this.md) değiştiriciye sahip olmalıdır.  
  
4. Çağıran kodda, uzantı yöntemi sınıfını içeren [ad alanını](../../language-reference/keywords/namespace.md) belirtmek için bir `using` yönergesi ekleyin.  
  
5. Yöntemleri, tür üzerinde örnek yöntemmiş gibi çağırın.  
  
     İlk parametrenin, işlecin uygulandığı türü temsil ettiğinden ve derleyicinin zaten nesnenizin türünü bildiği için kodu çağırarak belirtildiğine unutmayın. Parametreleri yalnızca 2 ' den `n`için bağımsız değişkenler sağlamanız gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `CustomExtensions.StringExtension` sınıfında `WordCount` adlı bir genişletme yöntemi uygular. Yöntemi, ilk yöntem parametresi olarak belirtilen <xref:System.String> sınıfında çalışır. `CustomExtensions` ad alanı uygulama ad alanına aktarılır ve yöntemi `Main` yönteminin içinde çağırılır.  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Uzantı yöntemleri, belirli bir güvenlik güvenlik açığı sunmaz. Tüm ad çakışmaları, türün kendisi tarafından tanımlanan örnek veya statik yöntem üzerinde çözümlendikleri için, bir tür üzerindeki mevcut yöntemlerin kimliğine bürünmek için hiçbir şekilde kullanılamaz. Genişletme metotları genişletilmiş sınıftaki herhangi bir özel veriye erişemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Genişletme Yöntemleri](./extension-methods.md)
- [LINQ (dil ile tümleşik sorgu)](../../linq/linq-in-csharp.md)
- [Statik Sınıflar ve Statik Sınıf Üyeleri](./static-classes-and-static-class-members.md)
- [protected](../../language-reference/keywords/protected.md)
- [internal](../../language-reference/keywords/internal.md)
- [public](../../language-reference/keywords/public.md)
- [this](../../language-reference/keywords/this.md)
- [namespace](../../language-reference/keywords/namespace.md)
