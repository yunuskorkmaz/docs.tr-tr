---
title: Özel uzatma yöntemi nasıl uygulanır ve çağrılır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: 7e2092a37c1f042a087e03f4a272139b585156c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705606"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a>Özel bir uzantı yöntemi (C# Programlama Kılavuzu) nasıl uygulanır ve çağrıyapılır?
Bu konu, herhangi bir .NET türü için kendi uzantı yöntemlerini nasıl uygulayacağınızı gösterir. İstemci kodu, bunları içeren DLL'ye bir başvuru ekleyerek ve uzantı yöntemlerinin tanımlandığı ad alanını belirten [bir kullanım](../../language-reference/keywords/using-directive.md) yönergesi ekleyerek uzantı yöntemlerinizi kullanabilir.  
  
## <a name="to-define-and-call-the-extension-method"></a>Uzantı yöntemini tanımlamak ve çağırmak için  
  
1. Uzantı yöntemini içerecek şekilde statik bir [sınıf](./static-classes-and-static-class-members.md) tanımlayın.  
  
     Sınıf istemci kodu için görünür olmalıdır. Erişilebilirlik kuralları hakkında daha fazla bilgi için [erişim değiştiricilere](./access-modifiers.md)bakın.  
  
2. Uzantı yöntemini, en azından içeren sınıfla aynı görünürlüğe sahip statik bir yöntem olarak uygulayın.  
  
3. Yöntemin ilk parametresi, yöntemin çalıştığı türü belirtir; [bu](../../language-reference/keywords/this.md) değiştirici ile önce olmalıdır.  
  
4. Arama kodunda, uzantı yöntemi sınıfını içeren ad `using` [alanını](../../language-reference/keywords/namespace.md) belirtmek için bir yönerge ekleyin.  
  
5. Yöntemleri, türdeki örnek yöntemleriymişgibi çağırın.  
  
     İlk parametrenin, işlecinin uygulandığı türü temsil ettiği ve derleyici nin nesnenizin türünü zaten bildiği için kod çağırılarak belirtilmedigini unutmayın. Sadece parametreler i 2 ile `n`2 için bağımsız değişkenler sağlamanız gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki `WordCount` `CustomExtensions.StringExtension` örnek, sınıfta adlı bir uzantı yöntemi uygular. Yöntem, ilk <xref:System.String> yöntem parametresi olarak belirtilen sınıf üzerinde çalışır. Ad `CustomExtensions` alanı uygulama ad alanına aktarılır ve `Main` yöntem yöntemin içinde çağrılır.  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Uzantı yöntemleri belirli bir güvenlik açığı sunmaz. Tüm ad çakışmaları, tür kendisi tarafından tanımlanan örnek veya statik yöntem lehine çözülür, çünkü bir tür de varolan yöntemleri taklit etmek için kullanılamaz. Uzantı yöntemleri genişletilmiş sınıftaki herhangi bir özel veriye erişemez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Genişletme Yöntemleri](./extension-methods.md)
- [LINQ (Dil-Entegre Sorgu)](../../linq/linq-in-csharp.md)
- [Statik Sınıflar ve Statik Sınıf Üyeleri](./static-classes-and-static-class-members.md)
- [protected](../../language-reference/keywords/protected.md)
- [Iç](../../language-reference/keywords/internal.md)
- [Kamu](../../language-reference/keywords/public.md)
- [bu](../../language-reference/keywords/this.md)
- [Namespace](../../language-reference/keywords/namespace.md)
