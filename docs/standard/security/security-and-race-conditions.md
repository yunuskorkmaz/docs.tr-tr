---
title: Güvenlik ve Yarış Durumları
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57ceaedc7c38ae70a0db5a7fd584a765a7474aff
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210500"
---
# <a name="security-and-race-conditions"></a>Güvenlik ve Yarış Durumları
Başka bir sorun olası güvenlik açıkları yarış koşulları tarafından kötüye alanıdır. Bu gerçekleşebilir birkaç yolu vardır. Aşağıdaki alt konuları Geliştirici kaçınmalısınız ana düşebileceğiniz tuzakları bazıları özetler.  
  
## <a name="race-conditions-in-the-dispose-method"></a>Dispose yöntemi yarış koşulları  
 Bir sınıf, ın **Dispose** yöntemi (daha fazla bilgi için bkz. [çöp toplama](../../../docs/standard/garbage-collection/index.md)) olan eşitlenmemiş, mümkündür içinde temizleme kodu **Dispose** çalıştırılabilir birden fazla Aşağıdaki örnekte gösterildiği gibi kez.  
  
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
  
 Çünkü bu **Dispose** uygulama eşitlenmemiş, mümkündür `Cleanup` ilk iş parçacığı ve önce ikinci bir iş parçacığı tarafından çağrılacak `_myObj` ayarlanır **null**. Bu bir güvenlik sorunu olup olmadığını bağlıdır ne olur olduğunda `Cleanup` kodu çalıştırır. Önemli bir sorun ile eşitlenmemiş **Dispose** uygulamaları dosyalar gibi kaynak tanıtıcıları kullanımını içerir. Hatalı elden çıkarma, genellikle güvenlik açıklarını müşteri adayları kullanılmak üzere yanlış tanıtıcı neden olabilir.  
  
## <a name="race-conditions-in-constructors"></a>Oluşturucularda yarış durumları  
 Bazı uygulamalarda, sınıf oluşturucuları tamamen çalıştırmadan önce sınıf üyelerinin erişmek diğer iş parçacıkları için mümkün olabilir. Bu durum veya gerekirse iş parçacığı eşitleme, hiçbir güvenlik sorunu olduğundan emin olmak için tüm sınıf oluşturucuları gözden geçirmeniz gerekir.  
  
## <a name="race-conditions-with-cached-objects"></a>Önbelleğe alınan nesneleri ile yarış durumları  
 Güvenlik bilgileri önbelleğe alır veya kod erişimi güvenliği kullanan kod [Assert](../../../docs/framework/misc/using-the-assert-method.md) işlem de olabilir yarış durumlarını savunmasız sınıfı diğer bölümlerini uygun şekilde eşitlenmemişse, aşağıdaki örnekte gösterildiği gibi.  
  
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
  
 Diğer yollara varsa `DoOtherWork` aynı nesneye sahip başka bir iş parçacığından çağrılabilir, güvenilmeyen bir çağıranın isteğe bağlı Koçan.  
  
 Kodunuzu güvenlik bilgilerini önbelleğe alıyorsa, bu güvenlik açığı için incelemeyi unutmayın.  
  
## <a name="race-conditions-in-finalizers"></a>Sonlandırıcılar yarış koşulları  
 Ardından nesnenin Sonlandırıcısı serbest bırakan bir statik veya yönetilmeyen kaynağa başvuran bir nesnedeki yarış durumları da meydana gelebilir. Nesneleri, birden çok nesne bir sınıfın Sonlandırıcı içinde yönetilen bir kaynak paylaşıyorsanız, tüm bu kaynağa erişimi eşitlemeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
