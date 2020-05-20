---
title: Temel Windows Workflow Kavramları
description: Bu makalede, bazı geliştiricilere alışkın olabilecek .NET Framework 4.6.1 iş akışı geliştirme kavramlarından bazıları açıklanmaktadır.
ms.date: 03/30/2017
ms.assetid: 0e930e80-5060-45d2-8a7a-95c0690105d4
ms.openlocfilehash: 07498241280191fb62a35a559a3391f7148c05b9
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419901"
---
# <a name="fundamental-windows-workflow-concepts"></a>Temel Windows Workflow Kavramları
İçinde iş akışı geliştirme, [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] bazı geliştiriciler için yeni olabilecek kavramları kullanır. Bu konuda bazı kavramlar ve bunların nasıl uygulandığı açıklanmaktadır.  
  
## <a name="workflows-and-activities"></a>İş akışları ve Etkinlikler  
 Bir iş akışı, bir işlemi modelleyen, yapılandırılmış bir eylem koleksiyonudur. İş akışındaki her eylem bir etkinlik olarak modellenir. Bir konak, bir iş akışını <xref:System.Activities.WorkflowInvoker> bir yöntem gibi çağırmak, <xref:System.Activities.WorkflowApplication> tek bir iş akışı örneğinin yürütülmesi üzerinde açık denetim için ve <xref:System.ServiceModel.WorkflowServiceHost> çok örnekli senaryolarda ileti tabanlı etkileşimler için kullanarak bir iş akışıyla etkileşime girer. İş akışının adımları bir etkinlik hiyerarşisi olarak tanımlandığından, hiyerarşideki en üstteki etkinlik iş akışının kendisini tanımlayabilirler. Bu hiyerarşi modeli, `SequentialWorkflow` önceki sürümlerden açık ve sınıfların yerini alır `StateMachineWorkflow` . Etkinlikler, diğer etkinliklerin koleksiyonları olarak geliştirilmiştir ( <xref:System.Activities.Activity> genellıkle xaml kullanılarak tanımlanır) veya sınıfı kullanılarak oluşturulur, <xref:System.Activities.CodeActivity> Bu da veri erişimi için çalışma zamanını kullanabilir veya <xref:System.Activities.NativeActivity> iş akışı çalışma zamanının kapsamını etkinlik yazarına sunan sınıfı kullanılarak oluşturulur. Ve kullanılarak geliştirilen etkinlikler <xref:System.Activities.CodeActivity> <xref:System.Activities.NativeActivity> , C# gıbı clr uyumlu diller kullanılarak oluşturulur.  
  
## <a name="activity-data-model"></a>Etkinlik veri modeli  
 Etkinlikler, aşağıdaki tabloda gösterilen türleri kullanarak verileri depolar ve paylaşır.  
  
|||  
|-|-|  
|Değişken|Verileri bir etkinlikte depolar.|  
|Bağımsız Değişken|Verileri bir etkinliğin içine ve dışına taşıın.|  
|İfade|Bağımsız değişken bağlamalarında yükseltilmiş bir dönüş değeri olan bir etkinlik.|  
  
## <a name="workflow-runtime"></a>İş akışı çalışma zamanı  
 İş akışı çalışma zamanı, iş akışlarının yürütüleceği ortamdır. <xref:System.Activities.WorkflowInvoker>, bir iş akışını yürütmek için en kolay yoldur. Ana bilgisayar <xref:System.Activities.WorkflowInvoker> aşağıdakiler için kullanır:  
  
- Bir iş akışını eşzamanlı olarak çağırmak için.  
  
- Bir iş akışından giriş sağlamak veya çıkış almak için.  
  
- Etkinlikler tarafından kullanılacak uzantıları eklemek için.  
  
 <xref:System.Activities.ActivityInstance>, konağın çalışma zamanı ile etkileşim kurmak için kullanabileceği, iş parçacığı güvenli proxy 'dir. Ana bilgisayar <xref:System.Activities.ActivityInstance> aşağıdakiler için kullanır:  
  
- Bir örneği oluşturarak veya bir örnek deposundan yükleyerek bir örnek elde etmek için.  
  
- Örnek yaşam döngüsü olayları hakkında bilgi almak için.  
  
- İş akışı yürütmeyi denetlemek için.  
  
- Bir iş akışından giriş sağlamak veya çıkış almak için.  
  
- Bir iş akışı devamlılığını bildirmek ve değerleri iş akışına geçirmek için.  
  
- İş akışı verilerini kalıcı hale getirme.  
  
- Etkinlikler tarafından kullanılacak uzantıları eklemek için.  
  
 Etkinlikler, veya gibi uygun türetilmiş sınıfı kullanarak iş akışı çalışma zamanı ortamına erişim elde edebilir <xref:System.Activities.ActivityContext> <xref:System.Activities.NativeActivityContext> <xref:System.Activities.CodeActivityContext> . Bu, alt etkinliklerin zamanlanması için ve diğer birçok amaçla bağımsız değişkenleri ve değişkenleri çözümlemek için bunu kullanırlar.  
  
## <a name="services"></a>Hizmetler  
 İş akışları, mesajlaşma etkinliklerini kullanarak, gevşek olarak bağlanmış Hizmetleri uygulamak ve erişmek için doğal bir yol sağlar. Mesajlaşma etkinlikleri WCF üzerine kurulmuştur ve bir iş akışının içine ve dışına veri almak için kullanılan birincil mekanizmadır. İstediğiniz her türlü ileti değişimi modelini modellemek için mesajlaşma etkinlikleri birlikte oluşturabilirsiniz. Daha fazla bilgi için bkz. [mesajlaşma etkinlikleri](../wcf/feature-details/messaging-activities.md). İş akışı hizmetleri sınıfı kullanılarak barındırılır <xref:System.ServiceModel.Activities.WorkflowServiceHost> . Daha fazla bilgi için bkz. [barındırma Iş akışı hizmetlerine genel bakış](../wcf/feature-details/hosting-workflow-services-overview.md). İş akışı hizmetleri hakkında daha fazla bilgi için bkz. [Workflow Services](../wcf/feature-details/workflow-services.md)  
  
## <a name="persistence-unloading-and-long-running-workflows"></a>Kalıcılık, kaldırma ve uzun süre çalışan Iş akışları  
 Windows Iş akışı, uzun süreli reaktif programların yazılmasını basitleştirerek şunları sağlar:  
  
- Dış girişe erişen etkinlikler.  
  
- <xref:System.Activities.Bookmark>Bir konak dinleyicisi tarafından devam ettirilebilecek nesneler oluşturma özelliği.  
  
- Bir iş akışının verilerini kalıcı hale getirme ve iş akışını kaldırma, sonra da iş akışını <xref:System.Activities.Bookmark> belirli bir iş akışındaki nesne sürdürme yanıt olarak yeniden etkinleştirebilir ve yeniden etkinleştirebilir.  
  
 Bir iş akışı, yürütülecek başka etkinlik olmayacak veya şu anda yürütülmekte olan tüm etkinlikler giriş için beklenene kadar etkinlikleri sürekli yürütür. Bu ikinci durumda iş akışı boşta kalır. Bir ana bilgisayar, boşta duran iş akışlarını kaldırmak ve bir ileti geldiğinde yürütmeye devam etmek için bunları yeniden yüklemek için yaygındır. <xref:System.ServiceModel.Activities.WorkflowServiceHost>Bu özellik için işlevsellik sağlar ve genişletilebilir bir kaldırma ilkesi sağlar. Geçici durum verileri veya kalıcı olmayan diğer verileri kullanan yürütme blokları için, bir etkinlik, kullanarak kalıcı olmaması gereken bir konağa işaret edebilir <xref:System.Activities.NoPersistHandle> . Bir iş akışı, etkinliğini kullanarak verileri dayanıklı bir depolama ortamına da açık bir şekilde kalıcı hale getirebilirler <xref:System.Activities.Statements.Persist> .
