---
description: 'Daha fazla bilgi edinin: Genişletilebilir nesneler'
title: Genişletilebilen Nesneler
ms.date: 03/30/2017
helpviewer_keywords:
- extensible objects [WCF]
ms.assetid: bc88cefc-31fb-428e-9447-6d20a7d452af
ms.openlocfilehash: 80082f4c94adf2d668ff4c241d286959d9a05038
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756701"
---
# <a name="extensible-objects"></a>Genişletilebilen Nesneler

Genişletilebilir nesne stili, mevcut çalışma zamanı sınıflarını yeni işlevlerle genişletmek veya bir nesneye yeni durum eklemek için kullanılır. Genişletilebilir nesnelerden birine bağlı olan uzantılar, paylaşılan durum ve işlevlere, bunlara erişebilen ortak bir Genişletilebilir nesneye eklenen işlevlere erişmek için işleme sırasındaki çok farklı aşamalar üzerinde davranışları etkinleştirin.

## <a name="the-iextensibleobjectt-pattern"></a>IExtensibleObject \<T> kalıbı

Genişletilebilir nesne deseninin üç arabirimi vardır: <xref:System.ServiceModel.IExtensibleObject%601> , <xref:System.ServiceModel.IExtension%601> ve <xref:System.ServiceModel.IExtensionCollection%601> .

<xref:System.ServiceModel.IExtensibleObject%601>Arabirim, nesnelerin işlevlerini özelleştirmesini sağlayan türler tarafından uygulanır <xref:System.ServiceModel.IExtension%601> .

Genişletilebilir nesneler nesnelerin dinamik toplanmasının kullanılmasına izin verir <xref:System.ServiceModel.IExtension%601> . <xref:System.ServiceModel.IExtension%601> nesneler aşağıdaki arabirimle belirlenir:

```csharp
public interface IExtension<T>
where T : IExtensibleObject<T>
{
    void Attach(T owner);
    void Detach(T owner);
}
```

Tür kısıtlaması, uzantıların yalnızca bir olan sınıflar için tanımlanabilir olmasını sağlar <xref:System.ServiceModel.IExtensibleObject%601> . <xref:System.ServiceModel.IExtension%601.Attach%2A> ve <xref:System.ServiceModel.IExtension%601.Detach%2A> toplama ya da ayırma bildirimleri sağlar.

Uygulamaların bir sahibe eklenip kaldırılabileceği kısıtlanması için geçerlidir. Örneğin, tamamen kaldırılmasına izin verebilir, sahip veya uzantı belirli bir durumda olduğunda uzantıları ekleme veya kaldırma, eşzamanlı olarak birden çok Sahibe ekleme veya tek bir eklemeyi yalnızca tek bir ekleme ve tek bir kaldırma ile izin verme.

<xref:System.ServiceModel.IExtension%601> , diğer standart yönetilen arabirimlere sahip herhangi bir etkileşim göstermez. Özellikle, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> sahip nesnesi üzerindeki yöntemi normalde uzantılarının bağlantısını içermez.

Koleksiyona bir uzantı eklendiğinde, <xref:System.ServiceModel.IExtension%601.Attach%2A> koleksiyona geçmeden önce çağrılır. Koleksiyondan bir uzantı kaldırıldığında, kaldırıldıktan <xref:System.ServiceModel.IExtension%601.Detach%2A> sonra çağrılır. Bu, bir uzantının ve arasında olduğu sırada yalnızca koleksiyonda bulunan üzerinde sayımda olabileceği anlamına gelir (uygun eşitlemeyi kabul ediyor <xref:System.ServiceModel.IExtension%601.Attach%2A> ) <xref:System.ServiceModel.IExtension%601.Detach%2A> .

Geçirilen <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> veya <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> olmayan nesne <xref:System.ServiceModel.IExtension%601> (örneğin, herhangi bir nesneyi geçirebilirsiniz), ancak döndürülen uzantı bir <xref:System.ServiceModel.IExtension%601> .

Koleksiyonda uzantı yoksa <xref:System.ServiceModel.IExtension%601> , <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> null döndürür ve <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> boş bir koleksiyon döndürür. Birden çok uzantı uygularsanız <xref:System.ServiceModel.IExtension%601> , bunlardan <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> birini döndürür. Öğesinden döndürülen değer <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> bir anlık görüntüdür.

İki ana senaryo vardır. İlk senaryo, <xref:System.ServiceModel.IExtensibleObject%601.Extensions%2A> bir nesne üzerinde durum eklemek için özelliği tür tabanlı sözlük olarak kullanır.

İkinci senaryo, <xref:System.ServiceModel.IExtension%601.Attach%2A> <xref:System.ServiceModel.IExtension%601.Detach%2A> bir nesnenin olayları kaydetme, durum geçişlerini izleme vb. gibi özel davranışa katılmasını sağlamak için ve özelliklerini kullanır.

<xref:System.ServiceModel.IExtensionCollection%601>Arabirim, <xref:System.ServiceModel.IExtension%601> türüne göre alma için izin veren nesnelerin bir koleksiyonudur <xref:System.ServiceModel.IExtension%601> . <xref:System.ServiceModel.IExtensionCollection%601.Find%2A?displayProperty=nameWithType> Bu türden bir olan en son eklenen nesneyi döndürür <xref:System.ServiceModel.IExtension%601> .

### <a name="extensible-objects-in-windows-communication-foundation"></a>Windows Communication Foundation Genişletilebilir nesneler

Windows Communication Foundation (WCF) üzerinde dört genişletilebilir nesne vardır:

- <xref:System.ServiceModel.ServiceHostBase> – Bu, hizmetin ana bilgisayar için temel sınıftır.  Bu sınıfın uzantıları, kendi davranışını genişletmek <xref:System.ServiceModel.ServiceHostBase> veya her bir hizmetin durumunu depolamak için kullanılabilir.

- <xref:System.ServiceModel.InstanceContext> – Bu sınıf hizmet çalışma zamanına sahip hizmet türünün bir örneğini bağlar.  Bu, örneği ve içeren bir başvuru hakkında bilgi içerir <xref:System.ServiceModel.InstanceContext> <xref:System.ServiceModel.ServiceHostBase> . Bu sınıfın uzantıları, <xref:System.ServiceModel.InstanceContext> her hizmet için durumu depolamak üzere veya davranışını genişletmek için kullanılabilir.

- <xref:System.ServiceModel.OperationContext> – Bu sınıf, çalışma zamanının her işlem için topladığı işlem bilgisini temsil eder.  Bu, gelen ileti üstbilgileri, gelen ileti özellikleri, gelen güvenlik kimliği ve diğer bilgiler gibi bilgileri içerir.  Bu sınıfın uzantıları, her bir işlemin davranışını genişletebilir <xref:System.ServiceModel.OperationContext> veya durum saklayabilir.

- <xref:System.ServiceModel.IContextChannel> – Bu arabirim, WCF çalışma zamanı tarafından oluşturulan kanalların ve proxy 'lerin her durumunun incelemesini sağlar.  Bu sınıfın uzantıları, <xref:System.ServiceModel.IClientChannel> her bir kanalın durumunu depolamak için ya da davranışını genişletebilir.

Aşağıdaki kod örneği, nesneleri izlemek için basit bir uzantının kullanımını gösterir <xref:System.ServiceModel.InstanceContext> .

[!code-csharp[IInstanceContextInitializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/iinstancecontextinitializer/cs/initializer.cs#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.IExtensibleObject%601>
- <xref:System.ServiceModel.IExtension%601>
- <xref:System.ServiceModel.IExtensionCollection%601>
