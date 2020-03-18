---
title: Güvenlik ve Yarış Durumları
'description:': Describes pitfalls to avoid around security holes exploited by race conditions, including dispose methods, constructors, cached objects, and finalizers.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
ms.openlocfilehash: 09d8d0d6e85af04fe0fb00f53df408126012081e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186786"
---
# <a name="security-and-race-conditions"></a>Güvenlik ve Yarış Durumları
Endişe edilen bir diğer konu da ırk koşullarının yararlanmış güvenlik açıkları potansiyeli. Bunun olabileceği çeşitli yollar vardır. İzleyen alt konular, geliştiricinin kaçınması gereken bazı önemli tuzakları sıralar.  
  
## <a name="race-conditions-in-the-dispose-method"></a>Elden Çıkarma Yönteminde Yarış Koşulları  
 Bir sınıfın **Elden Çıkarma** yöntemi (daha fazla bilgi için bkz. [Çöp Toplama)](../../../docs/standard/garbage-collection/index.md)eşitlenmemişse, Aşağıdaki örnekte gösterildiği **gibi, Elden Çıkarma** içindeki temizleme kodunun birden çok kez çalıştırılması mümkündür.  
  
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
  
 Bu **Elden Çıkarma** uygulaması eşitlenmediği için, `Cleanup` önce bir iş parçacığı tarafından çağrılması ve daha sonra ikinci bir iş parçacığının `_myObj` **null**olarak ayarlanmaması mümkündür. Bunun bir güvenlik sorunu olup `Cleanup` olmadığı, kod çalıştığında ne olduğuna bağlıdır. Eşitlenmemiş **Elden Çıkarma** uygulamalarıyla ilgili önemli bir sorun, dosyalar gibi kaynak iştamaçlarının kullanılmasıdır. Yanlış imha, yanlış tanıtıcının kullanılmasına neden olabilir ve bu da genellikle güvenlik açıklarına yol açar.  
  
## <a name="race-conditions-in-constructors"></a>İnşaatçılarda Yarış Koşulları  
 Bazı uygulamalarda, sınıf oluşturucuları tamamen çalışmadan önce diğer iş parçacıklarının sınıf üyelerine erişebilmeleri mümkün olabilir. Bu olması durumunda güvenlik sorunları olmadığından emin olmak için tüm sınıf oluşturucuları gözden geçirmeniz veya gerekirse iş parçacığı eşitleme niz gerekir.  
  
## <a name="race-conditions-with-cached-objects"></a>Önbelleğe Alınmış Nesnelerle Yarış Koşulları  
 Güvenlik bilgilerini önbelleğe alan veya kod erişim güvenliğini kullanan [kod,](../../../docs/framework/misc/using-the-assert-method.md) aşağıdaki örnekte gösterildiği gibi sınıfın diğer bölümleri uygun şekilde eşitlenmezse, ırk koşullarına karşı savunmasız da olabilir.  
  
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
  
 Aynı nesneye `DoOtherWork` sahip başka bir iş parçacığından çağrılabilen başka yollar varsa, güvenilmeyen bir arayan talebi niçin geçebilir.  
  
 Kodunuz güvenlik bilgilerini önbelleğe alırsa, bu güvenlik açığı için bu bilgileri gözden geçirdiğinizden emin olun.  
  
## <a name="race-conditions-in-finalizers"></a>Finalize'lerde Yarış Koşulları  
 Yarış koşulları, daha sonra sonlandırıcısında serbest kaldığı statik veya yönetilmeyen bir kaynağa başvuran bir nesnede de oluşabilir. Birden çok nesne, sınıfın sonlandırıcısında manipüle edilen bir kaynağı paylaşıyorsa, nesnelerin bu kaynağa tüm erişimi eşitlemesi gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
