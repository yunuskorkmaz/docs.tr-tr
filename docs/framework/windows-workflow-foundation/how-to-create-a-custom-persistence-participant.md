---
title: 'Nasıl yapılır: Özel Kalıcılık Katılımcısı Oluşturma'
ms.date: 03/30/2017
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
ms.openlocfilehash: 1de2abb8ababd794cd644733b6e4ab0ed42b1810
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321464"
---
# <a name="how-to-create-a-custom-persistence-participant"></a>Nasıl yapılır: Özel Kalıcılık Katılımcısı Oluşturma
Aşağıdaki yordam bir Kalıcılık Katılımcısı oluşturma adımları vardır. Bkz: [kalıcı katılan](https://go.microsoft.com/fwlink/?LinkID=177735) örnek ve [Store genişletilebilirlik](store-extensibility.md) konu Kalıcılık katılımcıları örnek uygulamaları için.  
  
1. Türetilen bir sınıf oluşturmanız <xref:System.Activities.Persistence.PersistenceParticipant> veya <xref:System.Activities.Persistence.PersistenceIOParticipant> sınıfı. PersistenceIOParticipant sınıfı g/ç işlemlerinde katılmak için ek olarak PersistenceParticipant sınıf olarak aynı genişletilebilirlik noktaları sağlar. Bir veya daha fazla aşağıdaki adımları izleyin.  
  
2. Uygulama <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> yöntemi. **CollectValues** iki sözlük parametreleri, okuma/yazma değerlerini depolamak için bir tane ve diğeri (daha sonra sorgularında kullanılan) salt yazılır değerleri depolamak için yöntemi vardır. Bu yöntemde özel Kalıcılık Katılımcısı veriler ile bu sözlük doldurmanız gerekir. Anahtar ve değer her sözlük değerin adını içeren olarak bir <xref:System.Runtime.DurableInstancing.InstanceValue> nesne.  
  
     ReadWriteValues sözlüğündeki değerleri olarak paketlenir **InstanceValue** nesneleri. Salt yazılır sözlüğündeki değerleri olarak paketlenir **InstanceValue** InstanceValueOptions.Optional ve InstanceValueOption.WriteOnly kümesiyle nesneleri. Her **InstanceValue** tarafından sağlanan **CollectValues** uygulamaları tüm Kalıcılık katılımcıları genelinde benzersiz adlara sahip olmalıdır.  
  
    ```  
    protected virtual void CollectValues (out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
3. Uygulama <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> yöntemi. **MapValues** yöntem parametreleri benzer iki parametre alır, **CollectValues** yöntemi alır. Toplanan tüm değerler **CollectValues** aşama Bu sözlük parametreleri gözden geçirilir. Tarafından eklenen yeni değerleri **MapValues** aşama salt yazılır değerlere eklenir.  Salt yazılır sözlük doğrudan örnek değerleri ile ilişkili bir dış kaynaktan veri sağlamak için kullanılır. Uygulamaları tarafından sağlanan her bir değeri **MapValues** yöntemi tüm Kalıcılık katılımcıları genelinde benzersiz adlara sahip olmalıdır.  
  
    ```  
    protected virtual IDictionary<XName,Object> MapValues (IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
     <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> Yöntem işlevselliği sağlar, <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> için bir bağımlılık tarafından işlenen edilmemiş başka bir Kalıcılık Katılımcısı tarafından sağlanan başka bir değer sağlar, daha önceden, <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> henüz.  
  
4. Uygulama **PublishValues** yöntemi. **PublishValues** yöntem sürdürme deposundan yüklenen tüm değerleri içeren bir sözlük alır.  
  
    ```  
    protected virtual void PublishValues (IDictionary<XName,Object> readWriteValues)  
    ```  
  
5. Uygulama **BeginOnSave** katılımcı bir g/ç Kalıcılık Katılımcısı varsa yöntemi. Bu yöntem, bir kayıt işlemi sırasında çağrılır. Bu yöntemde, iş akışı örnekleri (kaydetme) kalıcı hale getirmeniz için g/ç sunduğunuz gerçekleştirmeniz gerekir.  Konak bir işlem için karşılık gelen Kalıcılık komutu kullanıyorsanız, aynı işlem içinde Transaction.Current sağlanır.  Ayrıca, PersistenceIOParticipants biri değil Aksi takdirde kullanılacak içinde çalışması konak Kalıcılık bölüm için bir işlem oluşturur, bir işlem tutarlılığı gereksinim tanıtma.  
  
    ```  
    protected virtual IAsyncResult BeginOnSave (IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```  
  
6. Uygulama **BeginOnLoad** katılımcı bir g/ç Kalıcılık Katılımcısı varsa yöntemi. Bu yöntem, bir yükleme işlemi sırasında çağrılır. Bu yöntemde, iş akışı örnekleri yüklenmesini g/ç sunduğunuz gerçekleştirmeniz gerekir. Konak bir işlem için karşılık gelen Kalıcılık komutu kullanıyorsanız, aynı işlem içinde Transaction.Current sağlanır. Ayrıca, Kalıcılık g/ç katılımcıları biri değil Aksi takdirde kullanılacak içinde çalışması konak Kalıcılık bölüm için bir işlem oluşturur, bir işlem tutarlılığı gereksinim tanıtma.  
  
    ```  
    protected virtual IAsyncResult BeginOnLoad (IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```
