---
title: "Nasıl yapılır: özel Kalıcılık katılımcı oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d9cc47a-8966-4286-94d5-4221403d9c06
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e76c08586d45e09359b74d9c8cacdccef6f1ad13
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-custom-persistence-participant"></a>Nasıl yapılır: özel Kalıcılık katılımcı oluşturma
Aşağıdaki yordam Kalıcılık katılımcı oluşturmak için adım vardır. Bkz: [kalıcı katılan](http://go.microsoft.com/fwlink/?LinkID=177735) örnek ve [deposu genişletilebilirlik](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) konu Kalıcılık katılımcılarının örnek uygulamaları için.  
  
1.  Öğesinden türetilen bir sınıf oluşturun <xref:System.Activities.Persistence.PersistenceParticipant> veya <xref:System.Activities.Persistence.PersistenceIOParticipant> sınıfı. PersistenceIOParticipant sınıfı g/ç işlemlerinde katılmak için ek olarak PersistenceParticipant sınıf olarak aynı genişletilebilirlik noktaları sağlar. Bir veya daha fazla aşağıdaki adımları izleyin.  
  
2.  Uygulama <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> yöntemi. **CollectValues** yöntemi iki sözlük parametreleri, okuma/yazma değerlerini depolamak için bir tane ve diğeri (daha sonra sorgularda kullanılan) salt yazılır değerlerini depolamak için sahiptir. Bu yöntemde, bu sözlükler Kalıcılık Katılımcısı özgü verilerle doldurmanız gerekir. Anahtar ve değer her sözlük değeri adını içeren olarak bir <xref:System.Runtime.DurableInstancing.InstanceValue> nesnesi.  
  
     ReadWriteValues sözlüğündeki değerleri olarak paketlenir **InstanceValue** nesneleri. Salt yazılır sözlüğündeki değerleri olarak paketlenir **InstanceValue** InstanceValueOptions.Optional ve InstanceValueOption.WriteOnly kümesiyle nesneleri. Her **InstanceValue** tarafından sağlanan **CollectValues** uygulamaları tüm Kalıcılık katılımcılar arasında benzersiz bir adı olması gerekir.  
  
    ```  
    protected virtual void CollectValues (out IDictionary<XName,Object> readWriteValues, out IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
3.  Uygulama <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> yöntemi. **MapValues** yöntem parametreleri benzer iki parametre alır, **CollectValues** yöntemi alır. İçindeki tüm değerleri toplanan **CollectValues** aşaması, bu sözlük parametreleri gözden geçirilir. Tarafından eklenen yeni değerleri **MapValues** aşama salt yazılır değerlere eklenir.  Salt yazılır sözlük doğrudan örnek değerleri ile ilişkili bir dış kaynaktan veri sağlamak için kullanılır. Uygulamaları tarafından sağlanan her bir değeri **MapValues** yönteminin tüm Kalıcılık katılımcılar genelinde benzersiz bir ad olmalıdır.  
  
    ```  
    protected virtual IDictionary<XName,Object> MapValues (IDictionary<XName,Object> readWriteValues,IDictionary<XName,Object> writeOnlyValues)  
    ```  
  
     <xref:System.Activities.Persistence.PersistenceParticipant.MapValues%2A> Yöntemi işlevselliği sağlar, <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> başka bir değer tarafından işlenen kurmadı başka bir Kalıcılık katılımcılar tarafından sağlanan bir bağımlılığı sağlar, desteklemez, <xref:System.Activities.Persistence.PersistenceParticipant.CollectValues%2A> henüz.  
  
4.  Uygulama **PublishValues** yöntemi. **PublishValues** yöntemi Kalıcılık Mağazası'ndan yüklenen tüm değerleri içeren bir sözlük alır.  
  
    ```  
    protected virtual void PublishValues (IDictionary<XName,Object> readWriteValues)  
    ```  
  
5.  Uygulama **BeginOnSave** katılımcı Kalıcılık GÇ katılımcı ise yöntemi. Bu yöntem bir kaydetme işlemi sırasında çağrılır. Bu yöntemde, iş akışı örnekleri (kaydetme) sürdürmek için g/ç sunduğunuz gerçekleştirmeniz gerekir.  Konak bir işlem için karşılık gelen Kalıcılık komutu kullanıyorsanız, aynı işlem içinde Transaction.Current sağlanır.  Ayrıca, PersistenceIOParticipants bir Aksi durumda kullanılmıyorsa, çalışması konak Kalıcılık bölüm için bir işlem oluşturur. bir işlemsel tutarlılık gereksinim tanıtırsınız.  
  
    ```  
    protected virtual IAsyncResult BeginOnSave (IDictionary<XName,Object> readWriteValues, IDictionary<XName,Object> writeOnlyValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```  
  
6.  Uygulama **BeginOnLoad** katılımcı Kalıcılık GÇ katılımcı ise yöntemi. Bu yöntem, bir yükleme işlemi sırasında çağrılır. Bu yöntemde, iş akışı örnekleri yüklenmesini GÇ sunduğunuz gerçekleştirmeniz gerekir. Konak bir işlem için karşılık gelen Kalıcılık komutu kullanıyorsanız, aynı işlem içinde Transaction.Current sağlanır. Ek olarak, Kalıcılık GÇ katılımcıları bir Aksi durumda kullanılmıyorsa, çalışması konak Kalıcılık bölüm için bir işlem oluşturur. bir işlemsel tutarlılık gereksinim tanıtırsınız.  
  
    ```  
    protected virtual IAsyncResult BeginOnLoad (IDictionary<XName,Object> readWriteValues, TimeSpan timeout, AsyncCallback callback, Object state)  
    ```
