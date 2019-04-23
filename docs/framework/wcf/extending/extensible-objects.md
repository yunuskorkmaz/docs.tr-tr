---
title: Genişletilebilen Nesneler
ms.date: 03/30/2017
helpviewer_keywords:
- extensible objects [WCF]
ms.assetid: bc88cefc-31fb-428e-9447-6d20a7d452af
ms.openlocfilehash: 1af44f2394bbf27f9219831612b4e73d7a1759e1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220285"
---
# <a name="extensible-objects"></a>Genişletilebilen Nesneler
Genişletilebilir nesne düzeni ya da var olan çalışma zamanı sınıflar yeni işlevlerle genişletmek veya bir nesneye yeni bir durum eklemek için kullanılır. Genişletilebilen nesneler birine bağlı uzantılar, paylaşılan durum ve işlevselliği, erişimleri olan bir ortak Genişletilebilir nesnesine erişmek için işleme çok farklı aşamalarında davranışları etkinleştirin.  
  
## <a name="the-iextensibleobjectt-pattern"></a>IExtensibleObject\<T > deseni  
 Genişletilebilir nesne modelinde üç arabirimi vardır: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, ve <xref:System.ServiceModel.IExtensionCollection%601>.  
  
 <xref:System.ServiceModel.IExtensibleObject%601> Arabirimi sağlayan türleri tarafından uygulanan <xref:System.ServiceModel.IExtension%601> işlevleri özelleştirmek için nesneleri.  
  
 Genişletilebilen nesneler izin dinamik toplama <xref:System.ServiceModel.IExtension%601> nesneleri. <xref:System.ServiceModel.IExtension%601> nesneleri, aşağıdaki arabirim tarafından belirlenir:  
  
```  
public interface IExtension<T>  
where T : IExtensibleObject<T>  
{  
    void Attach(T owner);  
    void Detach(T owner);  
}  
```  
  
 Uzantılar yalnızca olan sınıflar için tanımlanabilir türü kısıtlaması garanti <xref:System.ServiceModel.IExtensibleObject%601>. <xref:System.ServiceModel.IExtension%601.Attach%2A> ve <xref:System.ServiceModel.IExtension%601.Detach%2A> toplama veya yükünün bildirim sağlar.  
  
 Bunlar eklenebilir ve bir sahibi gruptan kaldırılan olduğunda kısıtlamak uygulamaları için geçerlidir. Örneğin, ekleme engelleyerek kaldırma tamamen engelleyebilirsiniz veya eşzamanlı olarak birden fazla sahibe ekleme izin verme veya yalnızca tek bir kaldırma tarafından izlenen bir tek eklenmesine izin sahibi ya da uzantı belirli bir durumda olduğunda kaldırma uzantıları.  
  
 <xref:System.ServiceModel.IExtension%601> diğer standart yönetilen arabirimleri ile tüm etkileşimler anlamına gelmez. Özellikle, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> sahip nesne üzerinde değil normalde detach yöntemi uzantıları.  
  
 Bir uzantıyı koleksiyona eklendiğinde <xref:System.ServiceModel.IExtension%601.Attach%2A> koleksiyona geçmeden önce çağrılır. Uzantı, koleksiyondan kaldırıldığında <xref:System.ServiceModel.IExtension%601.Detach%2A> kaldırılmadan sonra çağrılır. Bunun bir uzantı anlamına gelir (uygun eşitleme varsayılarak) sayısı yalnızca, koleksiyondaki bulunamamasından üzerinde arasıdır <xref:System.ServiceModel.IExtension%601.Attach%2A> ve <xref:System.ServiceModel.IExtension%601.Detach%2A>.  
  
 Yönteme geçirilen nesne <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> veya <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> olmaması <xref:System.ServiceModel.IExtension%601> (örneğin, herhangi bir nesne geçirebilirsiniz), ancak döndürülen uzantısı bir <xref:System.ServiceModel.IExtension%601>.  
  
 Koleksiyondaki uzantısı ise bir <xref:System.ServiceModel.IExtension%601>, <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> null döndürür ve <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> boş bir koleksiyon döndürür. Birden fazla uzantı uygularsanız <xref:System.ServiceModel.IExtension%601>, <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> bunlardan birini döndürür. Döndürülen değer <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> anlık görüntüsüdür.
  
 İki ana senaryo vardır. İlk senaryoda kullanır <xref:System.ServiceModel.IExtensibleObject%601.Extensions%2A> özelliği olarak aramak bu türü kullanarak başka bir bileşen etkinleştirmek için bir nesne durumuna eklemek için türüne göre bir sözlük.  
  
 İkinci senaryoda kullanır <xref:System.ServiceModel.IExtension%601.Attach%2A> ve <xref:System.ServiceModel.IExtension%601.Detach%2A> durum geçişlerini izleme olayları'nın kaydedilmesi gibi özel davranış katılmak bir nesne etkinleştirmek ve benzeri için özellikleri.  
  
 <xref:System.ServiceModel.IExtensionCollection%601> Arabirimidir koleksiyonu <xref:System.ServiceModel.IExtension%601> almak için izin nesneleri <xref:System.ServiceModel.IExtension%601> türü tarafından. <xref:System.ServiceModel.IExtensionCollection%601.Find%2A?displayProperty=nameWithType> en son eklenen nesnesini döndürür bir <xref:System.ServiceModel.IExtension%601> türü.  
  
### <a name="extensible-objects-in-windows-communication-foundation"></a>Windows Communication Foundation'da genişletilebilen nesneler  
 Windows Communication Foundation (WCF) dört genişletilebilen nesneler vardır:  
  
-   <xref:System.ServiceModel.ServiceHostBase> – Bu hizmet ana bilgisayarı için temel sınıftır.  Bu sınıfın uzantıları, davranışını genişletmek için kullanılabilir <xref:System.ServiceModel.ServiceHostBase> kendisini veya her hizmet için durumu depolamak için.  
  
-   <xref:System.ServiceModel.InstanceContext> – Bu sınıf, hizmetin türünün bir örneği hizmet çalışma zamanı ile bağlanır.  Bir başvuru yanı sıra örneği hakkında bilgi içeren <xref:System.ServiceModel.InstanceContext>içeren uygulamanın <xref:System.ServiceModel.ServiceHostBase>. Bu sınıfın uzantıları, davranışını genişletmek için kullanılabilir <xref:System.ServiceModel.InstanceContext> veya her hizmet için durumu depolamak için.  
  
-   <xref:System.ServiceModel.OperationContext> – Bu sınıf, her işlem için çalışma zamanı toplar işlemi bilgileri temsil eder.  Bu, gelen ileti üstbilgileri, gelen ileti özelliklerini, gelen güvenlik kimliği ve diğer bilgileri gibi bilgileri içerir.  Bu sınıf uzantısı ya da davranışını genişletmek <xref:System.ServiceModel.OperationContext> veya her bir işlemin durumunu depolar.  
  
-   <xref:System.ServiceModel.IContextChannel> – Her durum için Kanallar ve WCF çalışma zamanı tarafından oluşturulan Proxy incelenmesi için bu arabirim sağlar.  Bu sınıf uzantısı ya da davranışını genişletmek <xref:System.ServiceModel.IClientChannel> veya her kanal için durumu depolamak için kullanabilirsiniz.  
  
-  
  
 Aşağıdaki kod örneği izlemek için basit bir uzantı kullanımını gösterir <xref:System.ServiceModel.InstanceContext> nesneleri.  
  
 [!code-csharp[IInstanceContextInitializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/iinstancecontextinitializer/cs/initializer.cs#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.IExtensibleObject%601>
- <xref:System.ServiceModel.IExtension%601>
- <xref:System.ServiceModel.IExtensionCollection%601>
