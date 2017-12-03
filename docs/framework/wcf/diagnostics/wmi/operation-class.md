---
title: "İşlem sınıfı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 492a3cb4b11706bfabc42976fb1adfad24a2279a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="operation-class"></a>İşlem sınıfı
Çalışma  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class Operation  
{  
  string Action;  
  boolean AsyncPattern;  
  Behavior Behaviors[];  
  boolean IsCallback;  
  boolean IsInitiating;  
  boolean IsOneWay;  
  boolean IsTerminating;  
  string MethodSignature;  
  string Name;  
  string ParameterTypes[];  
  string ReplyAction;  
  string ReturnType;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 İşlem sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 İşlem sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="action"></a>Eylem  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 İstek iletisinin WS adresleme eylem.  
  
### <a name="asyncpattern"></a>Başlatıcıda  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Zaman uyumsuz olarak kullanarak, bir işlem yapılmayacağını gösterir bir `Begin`[Aç/Kapat köşeli] ve `End`[Aç/Kapat açılı ayraçları] yöntem çiftinin bir hizmet sözleşmesinde.  
  
### <a name="behaviors"></a>Davranışlar  
 Veri türü: davranış dizisi  
  
 Erişim türüne: salt okunur  
  
 Bu işlemle ilişkili davranışlar.  
  
### <a name="iscallback"></a>IsCallback  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 İşlemi bir geri çağırma işlemi olduğunda true olur.  
  
### <a name="isinitiating"></a>IsInitiating  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Yöntemi sunucudaki bir oturum başlatabilirsiniz bir işlem uygulayan olup olmadığını gösterir.  
  
### <a name="isoneway"></a>IsOneWay  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Bir işlem bir yanıt iletisi döndürüp döndürmediğini gösterir.  
  
### <a name="isterminating"></a>IsTerminating  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Bir işlem bir yanıt iletisi döndürüp döndürmediğini gösterir.  
  
### <a name="methodsignature"></a>MethodSignature  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 İşlemi yöntemi imzası.  
  
### <a name="name"></a>Ad  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 İşlemin adı.  
  
### <a name="parametertypes"></a>ParameterTypes  
 Veri türü: dize dizisi  
  
 Erişim türüne: salt okunur  
  
 İşlemin parametre türleri.  
  
### <a name="replyaction"></a>ReplyAction  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 İşlem yanıt iletisi için SOAP eylemi değeri.  
  
### <a name="returntype"></a>ReturnType  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 İşlemin dönüş türü.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.OperationDescription>
