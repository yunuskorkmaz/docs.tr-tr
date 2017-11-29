---
title: "Genişletilebilen Nesneler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extensible objects [WCF]
ms.assetid: bc88cefc-31fb-428e-9447-6d20a7d452af
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 24482f97f5869def79ce2a24d33b3f9345d1c7c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="extensible-objects"></a>Genişletilebilen Nesneler
Genişletilebilir object deseni ya da varolan çalışma zamanı sınıflarını yeni işlevselliği ile genişletmek veya bir nesne için yeni durum eklemek için kullanılır. Genişletilebilen nesneler birine ekli uzantılar, paylaşılan durum ve bunlar erişebileceği bir ortak Genişletilebilir nesneye iliştirilmiş işlevlerine erişimini işleme çok farklı aşamalarında davranışları etkinleştirin.  
  
## <a name="the-iextensibleobjectt-pattern"></a>IExtensibleObject\<T > düzeni  
 Genişletilebilir nesne modelinde üç arabirimi vardır: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, ve <xref:System.ServiceModel.IExtensionCollection%601>.  
  
 <xref:System.ServiceModel.IExtensibleObject%601> Arabirimi izin türleri tarafından uygulanan <xref:System.ServiceModel.IExtension%601> işlevleri özelleştirmek için nesneleri.  
  
 Genişletilebilen nesneler, dinamik toplama izin <xref:System.ServiceModel.IExtension%601> nesneleri. <xref:System.ServiceModel.IExtension%601>nesneleri aşağıdaki arabirimi tarafından belirlenir:  
  
```  
public interface IExtension<T>  
where T : IExtensibleObject<T>  
{  
    void Attach(T owner);  
    void Detach(T owner);  
}  
```  
  
 Uzantıları olan sınıfları için yalnızca tanımlanabilir türü kısıtlama garanti <xref:System.ServiceModel.IExtensibleObject%601>. <xref:System.ServiceModel.IExtension%601.Attach%2A>ve <xref:System.ServiceModel.IExtension%601.Detach%2A> toplama veya yükünün bildirim sağlar.  
  
 Bunlar eklenebilir ve bir sahibinden kaldırılabilir zaman kısıtlamak uygulamaları için geçerli değil. Örneğin, ekleme vermemek kaldırma tamamen engelleyebilirsiniz veya aynı anda birden çok sahiplerine ekleme izin verme veya yalnızca tek bir Kaldır tarafından izlenen bir tek eklenmesine izin sahibi ya da uzantı belirli bir durumda olduğunda kaldırma uzantıları.  
  
 <xref:System.ServiceModel.IExtension%601>Standart diğer yönetilen arabirimleri ile herhangi bir etkileşimi göstermez. Özellikle, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> sahip nesne üzerinde değil normalde detach yöntemi uzantıları.  
  
 Uzantı koleksiyona eklendiğinde <xref:System.ServiceModel.IExtension%601.Attach%2A> koleksiyona geçmeden önce çağrılır. Uzantı koleksiyonundan kaldırıldığında <xref:System.ServiceModel.IExtension%601.Detach%2A> kaldırılmadan sonra çağrılır. Anlamına gelir (uygun eşitleme varsayılarak) bir uzantı sayısı yalnızca, koleksiyonda bulunamadı budur arasında <xref:System.ServiceModel.IExtension%601.Attach%2A> ve <xref:System.ServiceModel.IExtension%601.Detach%2A>.  
  
 Nesne geçirilen <xref:System.ServiceModel.IExtensionCollection%601.FindAll%60%601%2A> veya <xref:System.ServiceModel.IExtensionCollection%601.Find%60%601%2A> olmaması <xref:System.ServiceModel.IExtension%601> (örneğin, herhangi bir nesne geçirebilirsiniz), ancak döndürülen uzantısı bir <xref:System.ServiceModel.IExtension%601>.  
  
 Koleksiyondaki hiçbir uzantı ise bir <xref:System.ServiceModel.IExtension%601>, <xref:System.ServiceModel.IExtensionCollection%601.Find%60%601%2A> null döndürür ve <xref:System.ServiceModel.IExtensionCollection%601.FindAll%60%601%2A> boş bir koleksiyon döndürür. Birden çok uzantı uygularsanız <xref:System.ServiceModel.IExtension%601>, <xref:System.ServiceModel.IExtensionCollection%601.Find%60%601%2A> bunlardan birini döndürür. Döndürülen değer <xref:System.ServiceModel.IExtensionCollection%601.FindAll%60%601%2A> bir anlık görüntüdür.  
  
 İki ana senaryo vardır. İlk senaryoda kullanır <xref:System.ServiceModel.IExtensibleObject%601.Extensions%2A> özellik türü kullanılarak aramak başka bir bileşen etkinleştirmek için bir nesne üzerinde durumu eklemek için bir tür tabanlı sözlüğü olarak.  
  
 İkinci senaryo kullanan <xref:System.ServiceModel.IExtension%601.Attach%2A> ve <xref:System.ServiceModel.IExtension%601.Detach%2A> durumu geçişleri izleyen olaylar için kaydetme gibi özel davranış katılmak için bir nesne etkinleştirmek üzere özellikleri.  
  
 <xref:System.ServiceModel.IExtensionCollection%601> Arabirimidir koleksiyonu <xref:System.ServiceModel.IExtension%601> almak için izin nesneleri <xref:System.ServiceModel.IExtension%601> alt türe göre. <xref:System.ServiceModel.IExtensionCollection%601.Find%60%601%2A?displayProperty=nameWithType>döndürür en son eklenen nesne bir <xref:System.ServiceModel.IExtension%601> türü.  
  
### <a name="extensible-objects-in-windows-communication-foundation"></a>Windows Communication Foundation'da genişletilebilen nesneler  
 Dört Genişletilebilir nesneleri vardır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]:  
  
-   <xref:System.ServiceModel.ServiceHostBase>– Bu, hizmetin ana bilgisayar için temel sınıftır.  Bu sınıfın uzantıları davranışını genişletmek için kullanılabilir <xref:System.ServiceModel.ServiceHostBase> kendisini ya da her hizmet için durumu depolamak üzere.  
  
-   <xref:System.ServiceModel.InstanceContext>– Bu sınıf hizmet türünün bir örneği hizmeti çalışma zamanı ile bağlanır.  Örnek olarak bir başvuru hakkında bilgi içeren <xref:System.ServiceModel.InstanceContext>içeren <xref:System.ServiceModel.ServiceHostBase>. Bu sınıfın uzantıları davranışını genişletmek için kullanılabilir <xref:System.ServiceModel.InstanceContext> veya her hizmet için durumu depolamak üzere.  
  
-   <xref:System.ServiceModel.OperationContext>– Bu sınıf için her bir işlemin çalışma zamanı toplayan işlemi bilgileri temsil eder.  Bu gelen ileti üstbilgilerini, gelen ileti özellikleri, gelen güvenlik kimliği ve diğer bilgileri gibi bilgileri içerir.  Bu sınıf uzantıları ya da davranışını genişletmek <xref:System.ServiceModel.OperationContext> veya her bir işlemin durumu depolayın.  
  
-   <xref:System.ServiceModel.IContextChannel>– Bu arabirim tarafından oluşturulmuş proxy'leri ve kanallar için her durumu denetleme sağlar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çalışma zamanı.  Bu sınıf uzantıları ya da davranışını genişletmek <xref:System.ServiceModel.IClientChannel> veya her kanal için durumu depolamak için kullanabilirsiniz.  
  
-  
  
 Aşağıdaki kod örneğinde izlemek için basit bir uzantı kullanımını göstermektedir <xref:System.ServiceModel.InstanceContext> nesneleri.  
  
 [!code-csharp[IInstanceContextInitializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/iinstancecontextinitializer/cs/initializer.cs#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.IExtensibleObject%601>  
 <xref:System.ServiceModel.IExtension%601>  
 <xref:System.ServiceModel.IExtensionCollection%601>
