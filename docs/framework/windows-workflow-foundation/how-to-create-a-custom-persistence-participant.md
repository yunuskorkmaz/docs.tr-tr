---
title: 'Nasıl yapılır: Özel Kalıcılık Katılımcısı Oluşturma'
ms.date: 03/30/2017
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
ms.openlocfilehash: 47283375b618422d91a6279ee9049fae469f540a
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989678"
---
# <a name="how-to-create-a-custom-persistence-participant"></a>Nasıl yapılır: Özel Kalıcılık Katılımcısı Oluşturma
Aşağıdaki yordamda bir Kalıcılık Katılımcısı oluşturma adımları vardır. Kalıcılık katılımcılarının örnek uygulamaları için [Kalıcılık örneğine katılma](https://go.microsoft.com/fwlink/?LinkID=177735) ve [depolama genişletilebilirliği](store-extensibility.md) konusuna bakın.  
  
1. <xref:System.Activities.Persistence.PersistenceParticipant> Veya sınıfındantüretenbirsınıfoluşturun.<xref:System.Activities.Persistence.PersistenceIOParticipant> Persistenceıopmakalenipant sınıfı, g/ç işlemlerine katılabilmenin yanı sıra, Persistencekatılımcı sınıfıyla aynı genişletilebilirlik noktalarını sunar. Aşağıdaki adımlardan birini veya birkaçını izleyin.  
  
2. <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> Yöntemini uygulayın. **CollectValues** yönteminde, biri okuma/yazma değerlerini depolamak için ve diğeri salt yazılır değerlerini depolamak için bir tane olmak üzere iki sözlük parametresi vardır (daha sonra sorgularda kullanılır). Bu yöntemde, bu sözlükleri bir kalıcılık katılımcısına özgü verilerle doldurmanız gerekir. Her sözlük, anahtar olarak değerin adını ve değerini bir <xref:System.Runtime.DurableInstancing.InstanceValue> nesne olarak içerir.  
  
    ReadWriteValues sözlüğündeki değerler **InstanceValue** nesneleri olarak paketlenmiştir. Salt yazılır sözlükte bulunan değerler InstanceValueOptions. optional ve InstanceValueOption. WriteOnly kümesi ile **InstanceValue** nesneleri olarak paketlenir. Tüm Kalıcılık katılımcılarının üzerinde **CollectValues** uygulamaları tarafından belirtilen her **InstanceValue** benzersiz bir ada sahip olmalıdır.
  
    ```csharp  
    protected virtual void CollectValues(out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)
    {
    }
    ```  
  
3. <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> Yöntemini uygulayın. **MapValues** yöntemi, **CollectValues** yönteminin aldığı parametrelere benzer iki parametre alır. **CollectValues** aşamasında toplanan tüm değerler bu sözlük parametreleri aracılığıyla geçirilir. **MapValues** aşamasına göre eklenen yeni değerler salt yazılır değerlere eklenir.  Salt yazılır sözlük, örnek değerleriyle doğrudan ilişkili olmayan bir dış kaynağa veri sağlamak için kullanılır. Tüm Kalıcılık katılımcılarının içindeki **MapValues** yönteminin uygulamaları tarafından sunulan her bir değer benzersiz bir ada sahip olmalıdır.  
  
    ```csharp  
    protected virtual IDictionary<XName,Object> MapValues(IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)
    {
    }
    ```  
  
     Yöntemi, henüz işlenmemiş olan başka bir Kalıcılık Katılımcısı tarafından sağlanan başka bir değer üzerinde bir bağımlılığa izin verdiğinden, olmayan <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> işlevler sağlar. <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A>  
  
4. **PublishValues** yöntemini uygulayın. **PublishValues** yöntemi, kalıcılık deposundan yüklenen tüm değerleri içeren bir sözlük alır.  
  
    ```csharp  
    protected virtual void PublishValues(IDictionary<XName,Object> readWriteValues)
    {
    }
    ```  
  
5. Katılımcı bir kalıcılık g/ç katılımcısı ise, **BeginOnSave** yöntemini uygulayın. Bu yöntem, kaydetme işlemi sırasında çağrılır. Bu yöntemde, kalıcı (kaydetme) iş akışı örneklerine g/ç kolejinde gerçekleştirmelisiniz.  Ana bilgisayar karşılık gelen Kalıcılık komutu için bir işlem kullanıyorsa, Işlem. Current ' da aynı işlem sağlanır.  Ayrıca, Persistenceıopmakalenler, bir işlem tutarlılığı gereksinimi verebilir ve bu durumda konak, başka bir şekilde kullanılmıyorsa, kalıcılık bölümü için bir işlem oluşturur.  
  
    ```csharp  
    protected virtual IAsyncResult BeginOnSave(IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)
    {
    }
    ```  
  
6. Katılımcı bir kalıcılık g/ç katılımcısı ise, **BeginOnLoad** yöntemini uygulayın. Bu yöntem, yükleme işlemi sırasında çağrılır. Bu yöntemde, iş akışı örneklerinin yüklenmesi için g/ç kolejinde gerçekleştirmelisiniz. Ana bilgisayar karşılık gelen Kalıcılık komutu için bir işlem kullanıyorsa, Işlem. Current ' da aynı işlem sağlanır. Ayrıca, kalıcılık g/ç katılımcıları bir işlem tutarlılığı gereksinimi verebilir ve bu durumda konak, başka bir şekilde kullanılmıyorsa, kalıcılık bölümü için bir işlem oluşturur.  
  
    ```csharp  
    protected virtual IAsyncResult BeginOnLoad(IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)
    {
    }
    ```
