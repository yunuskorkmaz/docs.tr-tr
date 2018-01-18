---
title: "Güvenlik (LINQ-DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6116b2b8-75f4-4d8b-aea6-c13e55cda50b
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 305ff1232b21def3c8e7dcb1bec529f81c4e701a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="security-linq-to-dataset"></a>Güvenlik (LINQ-DataSet)
Bu konuda bulunan güvenlik sorunlarını ele alınmıştır [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].  
  
## <a name="passing-a-query-to-an-untrusted-component"></a>Güvenilmeyen bir bileşeni için bir sorgu geçirme  
 A [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorgu bir programı bir noktasında şeklide ve başka bir çalıştırılabilir. Sorgu burada şeklide noktada sorgu bu noktada, çağıran yönteme ait sınıfı ya da yerel değişkenleri/bağımsız değişkenlerini temsil eden simgeler gibi özel üyeleri tarafından görülebilir herhangi bir öğe başvuruda bulunabilir. Yürütme sırasında sorgu etkili bir şekilde çağıran kodu bunları görünürlüğe sahip olmayacağı olsa bile formülasyonu, sorgu tarafından başvurulan bu üyeler erişebilir olacaktır. Ne erişmek seçemezsiniz, sorguyu yürüten kodu rasgele eklenen görünürlük yok. Ne sorgu erişir, kesinlikle erişebilir ve yalnızca sorgu aracılığıyla.  
  
 Bu, bir sorgu için bir başvuru kod başka bir parçasını bileşen geçirerek sorgu alma erişimle tüm ortak ve özel üyeler, sorgunun başvurduğu güvenildiğini anlamına gelir. Genel olarak, [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] sorguları geçirilmedi güvenilmeyen bileşenler için böylece özel tutulmalıdır bilgi sağlamıyor sorgu dikkatli bir şekilde yapılandırılmış sürece.  
  
## <a name="external-input"></a>Dış giriş  
 Uygulamalar genellikle dış giriş (bir kullanıcı veya başka bir dış aracı) alın ve bu girişinize göre eylemleri gerçekleştirebilirsiniz.  Durumunda [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], uygulamanın bir dış giriş veya sorguda giriş kullanım dış göre belirli bir şekilde, bir sorgu oluşturun. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]Sorgu parametreleri değişmez değerleri kabul edildiğini her yerde kabul eder. Uygulama geliştiricilerinin injecting değişmez değerleri bir dış aracının yerine parametreli sorgular sorguyu doğrudan kullanmanız gerekir.  
  
 Herhangi bir giriş doğrudan veya dolaylı olarak kullanıcı veya bir dış aracı türetilmiş izinsiz eylemler gerçekleştirmek için hedef dili sözdizimi yararlanır içeriklere sahip olabilir. Bu hedef dil Transact-SQL olduğu bir saldırı desen sonra adlandırılmış bir SQL ekleme saldırısı olarak bilinir. Sorguyu doğrudan eklenen kullanıcı girişi bir veritabanı tablosu bırakın, hizmet reddine neden veya aksi halde gerçekleştirilmekte olan işlemin yapısını değiştirmek için kullanılır. Sorgu oluşturma mümkün olsa da [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], nesne modeli API'si gerçekleştirilir. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]dize düzenlemesi veya birleştirme, bunlar Transact-SQL ve SQL ekleme saldırıları geleneksel herkese açık şekilde etkilenmez gibi kullanarak sorguları oluşur değil.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Programlama Kılavuzu](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
