---
title: Güvenlik ve Yarış Durumları
'description:': Describes pitfalls to avoid around security holes exploited by race conditions, including dispose methods, constructors, cached objects, and finalizers.
ms.date: 07/15/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
ms.openlocfilehash: a667bf69ba72cbe203bd2603c4c6b7a1e58a6d43
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555116"
---
# <a name="security-and-race-conditions"></a>Güvenlik ve Yarış Durumları

Diğer bir konu alanı, yarış koşullarından yararlanılabilen güvenlik delikleri için olası bir konudur. Bunun gerçekleşebileceği çeşitli yollar vardır. İzleyen alt konu, geliştiricinin oluşmaması gereken önemli konuların bazılarını özetler.  
  
## <a name="race-conditions-in-the-dispose-method"></a>Dispose yönteminde yarış koşulları  

Bir sınıfın **Dispose** yöntemi (daha fazla bilgi için bkz. [çöp toplama](../garbage-collection/index.md)) eşitlenmemişse, **Dispose** içindeki temizleme kodu, aşağıdaki örnekte gösterildiği gibi birden çok kez çalıştırılabilir.  
  
```vb  
Sub Dispose()  
    If Not (myObj Is Nothing) Then  
       Cleanup(myObj)  
       myObj = Nothing  
    End If  
End Sub  
```  
  
```csharp  
void Dispose()
{  
    if (myObj != null)
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
Bu **Dispose** uygulamasının eşitlenmediği için `Cleanup` ilk bir iş parçacığı tarafından çağrılabilir ve daha önce ikinci bir iş parçacığı `_myObj` **null**olarak ayarlanmalıdır. Bunun bir güvenlik sorunu olup olmadığı, kod çalıştırıldığında ne olacağı hakkında farklılık gösterir `Cleanup` . Eşitlenmemiş **Dispose** uygulamalarıyla ilgili önemli bir sorun, dosyalar gibi kaynak tanıtıcılarının kullanımını içerir. Hatalı bırakma yanlış tanıtıcı kullanılmasına neden olabilir, bu da genellikle güvenlik açıklarına yol açar.  
  
## <a name="race-conditions-in-constructors"></a>Oluşturuculardaki yarış koşulları

Bazı uygulamalarda, sınıf oluşturucularının tamamen çalıştırılmasından önce diğer iş parçacıklarının sınıf üyelerine erişmesi mümkün olabilir. Bu durum oluşursa herhangi bir güvenlik sorunu olmadığından emin olmak için tüm sınıf oluşturucularını gözden geçirmeniz ve gerekirse iş parçacıklarını eşitlemeniz gerekir.  
  
## <a name="race-conditions-with-cached-objects"></a>Önbelleğe alınmış nesneleri olan yarış koşulları  

Aşağıdaki örnekte gösterildiği gibi, güvenlik bilgilerini önbelleğe alan veya kod erişimi güvenlik [onayı](../../framework/misc/using-the-assert-method.md) işlemini kullanan kod, sınıfın diğer kısımları uygun şekilde eşitlenmiyorsa yarış koşullarına açık de olabilir.  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False  
    End If  
End Sub  
  
Sub DoOtherWork()  
    If fCallersOK Then  
        DoSomethingTrusted()  
    Else  
        DemandSomething()  
        DoSomethingTrusted()  
    End If  
End Sub  
```  
  
```csharp  
void SomeSecureFunction()
{  
    if (SomeDemandPasses())
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false;  
    }  
}  
void DoOtherWork()
{  
    if (fCallersOK)
    {  
        DoSomethingTrusted();  
    }  
    else
    {  
        DemandSomething();  
        DoSomethingTrusted();  
    }  
}  
```  
  
`DoOtherWork`Aynı nesneye sahip başka bir iş parçacığından çağrılabilecek başka yollar varsa, güvenilmeyen bir arayan bir talebi geçmiş olabilir.  
  
Kodunuz güvenlik bilgilerini önbelleğe alıyorsa, bu güvenlik açığı için gözden geçirdiğinizden emin olun.  
  
## <a name="race-conditions-in-finalizers"></a>Sonlandırıcılar içindeki yarış koşulları  

Yarış koşulları, bir statik veya yönetilmeyen kaynağa başvuruda bulunan bir nesnede, daha sonra sonlandırıcıda boşaldığı bir nesne içinde de gerçekleşebilir. Birden çok nesne, bir sınıfın sonlandırıcıda yönetilen bir kaynağı paylaşıyorsa, nesnelerin bu kaynağa tüm erişimi eşitlemesi gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](secure-coding-guidelines.md)
- [ASP.NET Core güvenliği](/aspnet/core/security/)
